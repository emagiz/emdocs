---
id: combined-entry-connector-details
title: Combined entry connector details
sidebar_label: Combined entry connector details
---
#### Message type
The type of messages this entry connector handles.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

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

#### SOAP WS operation
The web service operation name for this message type.

#### Outbox
The JMS queue this entry connector produces messages on.

---
id: combined-entry-connector-details
title: Combined entry connector details
sidebar_label: Combined entry connector details
---
#### Message type
The type of messages this entry connector handles.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

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

#### SOAP WS operation
The web service operation name for this message type.

#### Outbox
The JMS queue this entry connector produces messages on.

