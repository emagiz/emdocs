# Naming conventions  

https://my.emagiz.com/link/documentation/8
In eMagiz there are a lot of things you have to (uniquely) name, for example: your configurations / message flows, your messaging components, your JMS queues, etc. While technically you could give them any name you like (e.g. "A1", "A2", "B1", etc), it is better to use some well thought-out naming conventions for the following reasons: 

  - you want to able to tell what something is and what function it provides based on the name
  - it shouldn't be hard to create a new name when you need one, but the result should be (fairly) unique
  - you want consistency in your names, especially when multiple people are working on the same project
  - the names should be "future proof": the naming scheme should be prepared for cases where your solution is expanded upon heavily in the future, even when initially it started as a very small project
 

What follows are the naming conventions used by eMagiz, which you might find useful to apply in your projects as well. First some general rules for naming are mentioned, followed by rules and examples of naming in specific contexts. Please note that these naming conventions are meant to help make naming easier, so take care not to complicate things by following these rules too strictly (there are always exceptions to the rules).

 
## General
 

  - All names are in English
  - Names should be short, but also self-explanatory
  - Use only lower case, as mixing upper and lower case can be confusing and not appropriate in all circumstances (e.g., URLs should be lower case)
  - Separate "categories" or "sub-types" in names by a decimal point ('.')
  - Separate words by a hyphen character ('-'), as spaces are usually not allowed in names
  - Do not use any other characters than letters ('a'-'z'), digits ('0'-'9'), decimal points ('.') or hyphens ('-') in names, as these characters are virtually guaranteed be be accepted by most (legacy) systems and do not conflict with the syntax of the most widely used formats in eMagiz (XML, property files, file names, etc)
  
# Configurations / message flows
 

For "stand-alone" or "point-to-point" connections, put the (abbreviated) system/customer name and message type/function in the configuration name. Some examples:

 

  - "hakron.orders"   (_handles orders from customer Hakron_)
  - "c1000.orders"   (_handles orders from customer C1000_)
  - "crs.bing-maps"   (_interface connecting system "CRS" to the Bing Maps API_)
  - "crs.google-maps"   (_interface connecting system "CRS" to the Google Maps API_)
 

For bus processes the type of process is also included in the name. Some examples:

 

  - "speakup.xmpp.entry"   (_entry connector for XMPP messages from SpeakUp_)
  - "speakup.xmpp.onramp"   (_onramp process for XMPP messages from SpeakUp_)
  - "csp.xmpp.offramp"   (_offramp process for XMPP messages to CSP_)
  - "csp.xmpp.exit"   (_exit connector for XMPP message to CSP_)
  - "csp.connector-infra"   (_common connector infrastructure for the CSP connectors_)
  - "csp.all.entry"   (_entry connector for all messages from CSP_)
  - "csp.mail.onramp"   (_onramp process for mail messages from CSP_)
  - "cape.routing.process"   (_routing process of the "CAPE" bus_)
  - "cape.error.process"   (_error process of the "CAPE" bus_)
  - "cape.jms-server-01"   (_JMS server #1 of the "CAPE" bus_)  
  
  
 # Messaging components
 

For message endpoints (these are all components that can be connected to one or more channels), describe what they do with the message. Some examples:
 

  - "speakup.xmpp.entry.receive.presence"   (_inbound channel adapter that receives XMPP presence messages from SpeakUp_)
  - "speakup.xmpp.entry.transform.presence-to-xml"   (_transformer that converts XMPP presence object messages from SpeakUp to XML_)
  - "cape.routing.process.route.by-message-type"   (_router in the "CAPE" bus routing process that routes messages based on their message type_)
  - "csp.xmpp.exit.filter.validate-message"   (_filter that validates XMPP messages send to CSP_)
  - "csp.xmpp.exit.transform.exception-to-error"   (_transformer that converts any exceptions that occur while connecting with CSP to error messages_)
  - "csp.xmpp.exit.send.error"   (_outbound channel adapters that sends error messages to the error process_)
 

For message channels, describe what type of messages they should contain. Some examples:

 

  - "speakup.xmpp.entry.channel.presence-obj"   (_channel containing XMPP presence object messages from SpeakUp_)
  - "speakup.xmpp.entry.channel.presence-xml"   (_channel containing XMPP presence XML messages from SpeakUp_)
  - "cape.routing.process.channel.csp-xmpp"   (_channel where XMPP messages for CSP get routed to_)
  - "csp.xmpp.exit.channel.message-unvalidated"   (_channel containing unvalidated XMPP messages to CSP_)
  - "csp.xmpp.exit.channel.message-validated"   (_channel containing validated XMPP messages to CSP_)
  - "csp.xmpp.exit.channel.exception"   (_channel where any exceptions that occur while connecting with CSP get send to_)
 

For support objects, describe the function it provides. Some examples:

 

  - "speakup.xmpp.entry.support.xmpp-connection"   (_the XMPP connection settings for connecting with SpeakUp_)
  - "cape.routing.process.support.jms-connection"   (_the JMS connection settings used by the routing process of the "CAPE" bus_)
  - "cape.jms-server-01.support.hornetq"   (_the HornetQ JMS server #1 of the "CAPE" bus_)
 

Note that in all cases the first part of the component name (everything up to the last decimal point) is automatically generated by the eMagiz flow designer, so the user only has to enter the last part of the name (everything after the last decimal point).

 

 # JMS queues
JMS queues are normally used to connect different bus processes, where every queue is the entry point of a single bus process. In this case the bus process name (see the "configuration name" section above) is an excellent choice for the JMS queue that is the entry point of that process. Some examples:

 

  - "jms.queue.async.speakup.xmpp.onramp"   (_entry queue for the asynchronous "speakup.xmpp.onramp" bus process_)
  - "jms.queue.async.csp.xmpp.offramp"   (_entry queue for the asynchronous "csp.xmpp.offramp" bus process_)
  - "jms.queue.async.csp.xmpp.exit"   (_entry queue for the asynchronous "csp.xmpp.exit" bus connector_)
  - "jms.queue.async.csp.mail.onramp"   (_entry queue for the asynchronous "csp.mail.onramp" bus process_)
  - "jms.queue.async.cape.routing"   (_entry queue for the asynchronous "cape.routing.process" bus process_)
  - "jms.queue.async.cape.error"   (_entry queue for the asynchronous "cape.error.process" bus process_)
 

Note that the first part of the JMS queue names ("jms.queue.") is automatically added by HornetQ (the default JMS implementation used by eMagiz), so the user only has to enter the last part of the name.

 

 # Java virtual machines
The JVM name should indicate the runtime type and it's function, for example:

 

  - "mendix.csp"   (_eMagiz running in a Mendix application called CSP; production environment_)
  - "mendix.csp-accp"   (_eMagiz running in a Mendix application called CSP; acceptance environment_)
  - "connector.speakup"   (_eMagiz running standalone, functioning as a connector to SpeakUp; production environment_)
  - "connector.zimbra"   (_eMagiz running standalone, functioning as a connector to Zimbra; production environment_)
  - "container.cape-01"   (_eMagiz running standalone, functioning as container #1 for bus processes of the "CAPE" bus; production environment_)
  - "container.cape-02"   (_eMagiz running standalone, functioning as container #2 for bus processes of the "CAPE" bus; production environment_)
  - "jms-server.cape-01"   (_eMagiz running standalone, functioning as JMS server #1 of the "CAPE" bus; production environment_)
  - "jms-server.cape-01-accp"   (_eMagiz running standalone, functioning as JMS server #1 of the "CAPE" bus; acceptance environment_)
  - "jms-server.cape-02"   (_eMagiz running standalone, functioning as JMS server #2 of the "CAPE" bus; production environment_)
  - "jms-server.cape-01b1"   (_eMagiz running standalone, functioning as backup #1 for JMS server #1 of the "CAPE" bus; production environment_)
 

Note that in contrast to names in all the other contexts, the JVM names _do_ need a distinction between DTAP modes because you want to have different settings for your message flows depending on the environment. This is something you configure on the JVM level, but all other contexts shouldn't be aware of their environment (e.g., you don't want to create separate message flows for acceptance and production, as this would defeat the purpose of the acceptance test).

 

 # Properties
Specify the target system/customer, protocol and function in the property name, for example:

 

  - "cape.jms.host"   (_host name for connecting to the "CAPE" bus using JMS_)
  - "cape.jms.port"   (_port number for connecting to the "CAPE" bus using JMS_)
  - "cape.jms.username"   (_user name for connecting to the "CAPE" bus using JMS_)
  - "cape.ws.url"   (_URL for connecting to the "CAPE" bus using web services_)
  - "cape.ws.username"   (_user name for connecting to the "CAPE" bus using web services_)
  - "speakup.xmpp.host"   (_host name for connecting to SpeakUp using XMPP_)
  - "speakup.xmpp.username"   (_user name for connecting to SpeakUp using XMPP_)
  - "companya.ftp.host"   (_host name for connecting to "Company A" using FTP_)
  - "companyb.ftp.host"   (_host name for connecting to "Company B" using FTP)
  - "companyb.ftp.pickup.directory"   (_directory for reading files from "Company B" using FTP_)
  - "companyb.file.pickup.directory"   (_directory for reading files from "Company B" using 'local' files_)
  - "companyb.file.pickup.pattern"   (_file name pattern for reading files from "Company B" using 'local' files_)
  - "companyb.file.drop.directory"   (_directory for writing files for "Company B" using 'local' files_)
 

 # XML namespaces
An XML namespace is basically just a unique string value, but to guarantee that values are globally unique, the convention is to use an HTTP URL of your own company. To make sure the value is unique within that domain, you can use the following format for XML namespaces: http://www.yourdomain.com/ns/app/service/version/ (the underlined words should be replaced by actual values). Some examples:

 

  - "http://www.companya.com/ns/portal/order-entry/1.0/"   (_a Mendix portal hosted by "Company A" that exposes web services in the "Order Entry" module_)
  - "http://www.companyb.nl/ns/cdm/1.0/"   (_version 1.0 of the Common Data Model of "Company B"_)
  - "http://www.companyb.nl/ns/emagiz/crm/1.0/"   (_interface provided by an eMagiz project running at "Company B" that connects to their CRM system_)
 

If you need to make any changes in a namespace definition that's already being used, you should increase the version number. This way, it's clear what the newer definition is, but it still allows the older definition to be used at the same time. This allows for having multiple (legacy) versions of an interface running at the same time, providing backwards compatibility for older systems that can't easily update their interfaces.

 

 # Resources / file names
For XSDs, you can easily base the file name on the namespace it defines as follows:

 

  - "companya-portal-order-entry-1.0.xsd"   (_based on namespace "http://www.companya.com/ns/portal/order-entry/1.0/" _)
  - "companyb-cdm-1.0.xsd"   (_based on namespace "http://www.companyb.nl/ns/cdm/1.0/" _)
  - "companyb-emagiz-crm-1.0.xsd"   (_based on namespace "http://www.companyb.nl/ns/emagiz/crm/1.0/" _)
 

For XSLTs, describe the function of the transformation it performs. Some examples:

 

  - "hakron-orders-to-cdm.xsl"   (_transforms orders from Hakron to CDM format_)
  - "cdm-to-hakron-orders.xsl"   (_transforms orders from CDM to Hakron format_)
  - "crs-to-google-maps.xsl"   (_transforms from CRS to Google Maps API format_)
 

For property files, base the name on the JVM or eMagiz configuration that uses the properties as follows:

 

  - "connector-speakup.properties"   (_contains properties used by all configurations running in JVM "connector.speakup"_)
  - "container-cape-01.properties"   (_contains properties used by all configurations running in JVM "container.cape-01"_)
  - "hakron-orders.properties"   (_contains properties used solely by eMagiz configuration "hakron.orders"_)
 

For eMagiz configuration files, base the file name on the name of that configuration as follows (this is also the default name when downloading configurations from the eMagiz flow designer):

 

  - "hakron-orders.enc"   (_file containing encrypted configuration "hakron.orders"_)
  - "speakup-xmpp-entry.enc"   (_file containing encrypted configuration "speakup.xmpp.entry"_)
  - "cape-error-process.xml"   (_file containing non-encrypted configuration "cape.error.process"_)
 

Note that with all file names most decimal points ('.') are replaced by a hyphen character ('-'), because the decimal point usually indicates a file extension in file names.
