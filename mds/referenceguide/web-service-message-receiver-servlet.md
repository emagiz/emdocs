---
id: web-service-message-receiver-servlet
title: Web service message receiver servlet
sidebar_label: Web service message receiver servlet
---
#### Delegates all request handling to the specified Web Service Message Receiver.
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/server.html#message-dispatcher-servlet" target="_blank">External documentation</a>

A Http Servlet implementation that delegates all request handling to the specified Spring Web Services Web Service Message Receiver.

(Advanced)
It also offers a way to expose WSDL to clients. Another option is to let Spring Web Services generate a WSDL from an XSD schema.


#### Message receiver
Web Service Message Receiver that is used for handling the incoming messages.

#### Message factory
Defines which message factory is used  for converting the incoming Http Servlet Request into a Web Service Message

#### Transform WSDL locations
Specifies whether relative address locations in the WSDL are to be transformed using the request URI of the incoming HttpServletRequest

Default is false

#### WSDL location expression
The location of the WSDL file to expose, as a Spring resource location: a URL, a "classpath:" pseudo URL, or a relative file path.


WSDL definitions to be exposed by this webservice servlet.

They will be exposed on the URL of this servlet, appended with the name of the definition + <code>.wsdl</code> suffix.

Note that exposing the WSDL is not required for the web service to function, it only makes the definition (publicly) available.


XSD schemas to be exposed by this webservice servlet.

They will be exposed on the URL of this servlet, appended with the name of the schema + <code>.xsd</code> suffix.

Note that exposing the XSD is not required for the web service to function, it only makes the schema (publicly) available.


Mendix service definitions to be exposed by this webservice servlet.

They will be exposed on the URL of this servlet, appended with the name of the definition + <code>.msd</code> suffix.

Note that exposing the MSD is not required for the Mendix app service to function, it only makes the definition (publicly) available.

---
id: web-service-message-receiver-servlet
title: Web service message receiver servlet
sidebar_label: Web service message receiver servlet
---
#### Delegates all request handling to the specified Web Service Message Receiver.
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/server.html#message-dispatcher-servlet" target="_blank">Documentation</a>

A Http Servlet implementation that delegates all request handling to the specified Spring Web Services Web Service Message Receiver.

(Advanced)
It also offers a way to expose WSDL to clients. Another option is to let Spring Web Services generate a WSDL from an XSD schema.


#### Message receiver
Web Service Message Receiver that is used for handling the incoming messages.

#### Message factory
Defines which message factory is used  for converting the incoming Http Servlet Request into a Web Service Message

#### Transform WSDL locations
Specifies whether relative address locations in the WSDL are to be transformed using the request URI of the incoming HttpServletRequest

Default is false

#### WSDL location expression
The location of the WSDL file to expose, as a Spring resource location: a URL, a "classpath:" pseudo URL, or a relative file path.


WSDL definitions to be exposed by this webservice servlet.

They will be exposed on the URL of this servlet, appended with the name of the definition + <code>.wsdl</code> suffix.

Note that exposing the WSDL is not required for the web service to function, it only makes the definition (publicly) available.


XSD schemas to be exposed by this webservice servlet.

They will be exposed on the URL of this servlet, appended with the name of the schema + <code>.xsd</code> suffix.

Note that exposing the XSD is not required for the web service to function, it only makes the schema (publicly) available.

