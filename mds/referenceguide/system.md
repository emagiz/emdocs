---
id: system
title: System
sidebar_label: System settings
---

Here you can:
- Name the system you want to integrate
- Describe the system
- Give additional remarks

---
id: system
title: System
sidebar_label: System
---
#### System
Unique name for this system.

This value needs to match exactly the value used in the calls to the mapping web services that are made from eMagiz message flows.

<i>Required</i>

### 
Unique name for this system.

This value needs to match exactly the value used in the calls to the mapping web services that are made from eMagiz message flows.

<i>Required</i>

#### Mendix connector
On if this system is a Mendix application using the MendixConnector module to connect to the message bus.

The MendixConnector has limited settings and therefore no visual flows. Its settings are largely generated automatically.

#### SOAP WS namespace
The namespace for the exposed web service.

#### Combined entry connector
Normally, one connector is generated per system that contains multiple <i>entry flows</i> (one for each message type). In some cases however, it is required that all these flows are combined into one big configuration, usually to be able to share resources.

For example, when exposing the connector as a SOAP web service, you probably want all different incoming message types to be hosted as different web service operations combined into a <i>single</i> web service (i.e., one HTTP server, one port that needs to be accessible, and one WSDL).

#### Entry connector type
The type of combined entry connector. This determines how the flows are generated:

<b>SOAP web service</b>: This generates a fully configured Jetty web server hosting a single web service, containing one operation for each message type. The incoming messages are then extracted from the SOAP message and placed on the correct JMS queue.

<b>Custom</b>: This generates a fully configured flow endpoint for each message type, and lets the user define the starting points of these flows.

#### SOAP WS name
Name for the exposed web service as used in the web service URL.

The full URL of the WSDL will look as follows (the underlined words need to be replaced by the actual values):
<code>http://<u>host</u>:<u>port</u>/ws/<u>ws-name</u>/<u>ws-name</u>.wsdl</code>

#### SOAP WS namespace
The namespace for the exposed web service.

#### Multi-instance
Whether or not this system's connector will be deployed multiple times. For this to work, tenants have to be added to the system. One runtime instance will be created for every tenant, instead of a single runtime for the system.

#### Mendix connector
On if this system is a Mendix application using the MendixConnector module to connect to the message bus.

The MendixConnector has limited settings and therefore no visual flows. Its settings are largely generated automatically.

#### SOAP WS namespace
The namespace for the exposed web service.

#### Combined entry connector
Normally, one connector is generated per system that contains multiple <i>entry flows</i> (one for each message type). In some cases however, it is required that all these flows are combined into one big configuration, usually to be able to share resources.

For example, when exposing the connector as a SOAP web service, you probably want all different incoming message types to be hosted as different web service operations combined into a <i>single</i> web service (i.e., one HTTP server, one port that needs to be accessible, and one WSDL).

#### Entry connector type
The type of combined entry connector. This determines how the flows are generated:

<b>SOAP web service</b>: This generates a fully configured Jetty web server hosting a single web service, containing one operation for each message type. The incoming messages are then extracted from the SOAP message and placed on the correct JMS queue.

<b>Custom</b>: This generates a fully configured flow endpoint for each message type, and lets the user define the starting points of these flows.

#### SOAP WS name
Name for the exposed web service as used in the web service URL.

The full URL of the WSDL will look as follows (the underlined words need to be replaced by the actual values):
<code>http://<u>host</u>:<u>port</u>/ws/<u>ws-name</u>/<u>ws-name</u>.wsdl</code>

#### SOAP WS namespace
The namespace for the exposed web service.

#### Multi-instance
Whether or not this system's connector will be deployed mulitple times. For this to work, tenants have to be added to the system. One runtime instance will be created for every tenant, instead of a single runtime for the system.

#### Display name
Display name for this system.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the system, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Additional information
Additional informationabout the system. For example this can include a name and phone number of a contact person.

#### Display name
Display name for this system.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the system, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Additional information
Additional informationabout the system. For example this can include a name and phone number of a contact person.

