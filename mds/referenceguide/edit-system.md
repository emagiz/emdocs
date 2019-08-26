---
id: edit-system
title: Edit System
sidebar_label: Edit System
---
### 
Display name for this system.

This value is used for displaying in the GUI only.

### 
Abbreviated name of the system, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

### 
Turn this on if the system is a Mendix application using the MendixConnector module to connect to the message bus.

The MendixConnector has limited settings and therefore no visual flows. Its settings are largely generated automatically.

### 
The namespace for the exposed web service.

To let eMagiz generate a namespace for you, first enter bus settings and system name.

### 
Normally, one connector is generated per system that contains multiple <i>entry flows</i> (one for each message type). In some cases however, it is required that all these flows are combined into one big configuration, usually to be able to share resources.

For example, when exposing the connector as a SOAP web service, you'd probably want all different incoming message types to be hosted as different web service operations combined into a <i>single</i> web service (i.e., one HTTP server, one port that needs to be accessible and one WSDL).

### 
The type of combined entry connector. This determines how the flows are generated:

<b>SOAP web service</b>: This generates a fully configured Jetty web server hosting a single web service, containing one operation for each message type. The incoming messages are then extracted from the SOAP message and placed on the correct JMS queue.

### 
Name for the exposed web service as used in the web service URL.

The full URL of the WSDL will look as follows (the underlined words need to be replaced by the actual values):
<code>http://<u>host</u>:<u>port</u>/ws/<u>ws-name</u>/<u>ws-name</u>.wsdl</code>

### 
Whether or not this system's connector will be deployed mulitple times. For this to work, tenants have to be added to the system. One runtime instance will be created for each tenant, instead of a single runtime for the system.

### 
Determines the amount of runtimes for this system in the Deploy phase. Can be used to increase availability for HA cases (high availability), such as AWS with failover.

Should only be used together with HA bus settings.

When used together with mulit-instance tenants, this amount of runtimes is created per tenant.

### 
Display name for this system.

This value is used for displaying in the GUI only.

### 
Abbreviated name of the system, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

### 
Turn this on if the system is a Mendix application using the MendixConnector module to connect to the message bus.

The MendixConnector has limited settings and therefore no visual flows. Its settings are largely generated automatically.

### 
The namespace for the exposed web service.

### 
Normally, one connector is generated per system that contains multiple <i>entry flows</i> (one for each message type). In some cases however, it is required that all these flows are combined into one big configuration, usually to be able to share resources.

For example, when exposing the connector as a SOAP web service, you'd probably want all different incoming message types to be hosted as different web service operations combined into a <i>single</i> web service (i.e., one HTTP server, one port that needs to be accessible and one WSDL).

### 
The type of combined entry connector. This determines how the flows are generated:

<b>SOAP web service</b>: This generates a fully configured Jetty web server hosting a single web service, containing one operation for each message type. The incoming messages are then extracted from the SOAP message and placed on the correct JMS queue.

<b>Custom</b>: This generates a fully configured flow endpoint for each message type, and lets the user define the starting points of these flows.

### 
Name for the exposed web service as used in the web service URL.

The full URL of the WSDL will look as follows (the underlined words need to be replaced by the actual values):
<code>http://<u>host</u>:<u>port</u>/ws/<u>ws-name</u>/<u>ws-name</u>.wsdl</code>

### 
The namespace for the exposed web service.

### 
Whether or not this system's connector will be deployed mulitple times. For this to work, tenants have to be added to the system. One runtime instance will be created for each tenant, instead of a single runtime for the system.

### 
Determines the amount of runtimes for this system in the Deploy phase. Can be used to increase availability for HA cases (high availability), such as AWS with failover.

Should only be used together with HA bus settings.

When used together with mulit-instance tenants, this amount of runtimes is created per tenant.

---
id: edit-system
title: Edit System
sidebar_label: Edit System
---
### 
Display name for this system.

This value is used for displaying in the GUI only.

### 
Abbreviated name of the system, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

### 
Turn this on if the system is a Mendix application using the MendixConnector module to connect to the message bus.

The MendixConnector has limited settings and therefore no visual flows. Its settings are largely generated automatically.

### 
The namespace for the exposed web service.

To let eMagiz generate a namespace for you, first enter bus settings and system name.

### 
Normally, one connector is generated per system that contains multiple <i>entry flows</i> (one for each message type). In some cases however, it is required that all these flows are combined into one big configuration, usually to be able to share resources.

For example, when exposing the connector as a SOAP web service, you'd probably want all different incoming message types to be hosted as different web service operations combined into a <i>single</i> web service (i.e., one HTTP server, one port that needs to be accessible and one WSDL).

### 
The type of combined entry connector. This determines how the flows are generated:

<b>SOAP web service</b>: This generates a fully configured Jetty web server hosting a single web service, containing one operation for each message type. The incoming messages are then extracted from the SOAP message and placed on the correct JMS queue.

### 
Name for the exposed web service as used in the web service URL.

The full URL of the WSDL will look as follows (the underlined words need to be replaced by the actual values):
<code>http://<u>host</u>:<u>port</u>/ws/<u>ws-name</u>/<u>ws-name</u>.wsdl</code>

### 
Whether or not this system's connector will be deployed mulitple times. For this to work, tenants have to be added to the system. One runtime instance will be created for each tenant, instead of a single runtime for the system.

### 
Determines the amount of runtimes for this system in the Deploy phase. Can be used to increase availability for HA cases (high availability), such as AWS with failover.

Should only be used together with HA bus settings.

When used together with mulit-instance tenants, this amount of runtimes is created per tenant.

### 
Display name for this system.

This value is used for displaying in the GUI only.

### 
Abbreviated name of the system, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

### 
Turn this on if the system is a Mendix application using the MendixConnector module to connect to the message bus.

The MendixConnector has limited settings and therefore no visual flows. Its settings are largely generated automatically.

### 
The namespace for the exposed web service.

### 
Normally, one connector is generated per system that contains multiple <i>entry flows</i> (one for each message type). In some cases however, it is required that all these flows are combined into one big configuration, usually to be able to share resources.

For example, when exposing the connector as a SOAP web service, you'd probably want all different incoming message types to be hosted as different web service operations combined into a <i>single</i> web service (i.e., one HTTP server, one port that needs to be accessible and one WSDL).

### 
The type of combined entry connector. This determines how the flows are generated:

<b>SOAP web service</b>: This generates a fully configured Jetty web server hosting a single web service, containing one operation for each message type. The incoming messages are then extracted from the SOAP message and placed on the correct JMS queue.

<b>Custom</b>: This generates a fully configured flow endpoint for each message type, and lets the user define the starting points of these flows.

### 
Name for the exposed web service as used in the web service URL.

The full URL of the WSDL will look as follows (the underlined words need to be replaced by the actual values):
<code>http://<u>host</u>:<u>port</u>/ws/<u>ws-name</u>/<u>ws-name</u>.wsdl</code>

### 
The namespace for the exposed web service.

### 
Whether or not this system's connector will be deployed mulitple times. For this to work, tenants have to be added to the system. One runtime instance will be created for each tenant, instead of a single runtime for the system.

### 
Determines the amount of runtimes for this system in the Deploy phase. Can be used to increase availability for HA cases (high availability), such as AWS with failover.

Should only be used together with HA bus settings.

When used together with mulit-instance tenants, this amount of runtimes is created per tenant.

