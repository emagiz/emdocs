---
id: integration
title: Integration
sidebar_label: Integration
---
### 
The web service operation name for this message type.

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
Normally, if a system consumes and produces messages, separate entry and exit connector flows are used for connecting the system to the message bus.

In some cases however, the consumption of a message also produces a message as the result. If these messages can be handled by asynchronous message flows but there is a need to somehow correlate them, use an <i>exit/entry connector</i>: this generates an <i>exit connector</i> that delivers messages to the consuming system, that also acts like an <i>entry connector</i> by placing messages produced by that same system back onto the message bus.

### 
The type of messages that are send back to the message bus by the <i>exit/entry connector</i>.

### 
The type of messages that are send to the connected system by the <i>exit/entry connector</i>, that result in the messages send back to the message bus handled by this offramp process.

### 
The web service operation name for this message type.

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
Normally, if a system consumes and produces messages, separate entry and exit connector flows are used for connecting the system to the message bus.

In some cases however, the consumption of a message also produces a message as the result. If these messages can be handled by asynchronous message flows but there is a need to somehow correlate them, use an <i>exit/entry connector</i>: this generates an <i>exit connector</i> that delivers messages to the consuming system, that also acts like an <i>entry connector</i> by placing messages produced by that same system back onto the message bus.

### 
The type of messages that are send back to the message bus by the <i>exit/entry connector</i>.

### 
The type of messages that are send to the connected system by the <i>exit/entry connector</i>, that result in the messages send back to the message bus handled by this offramp process.

---
id: integration
title: Integration
sidebar_label: Integration
---
### 
The web service operation name for this message type.

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
Normally, if a system consumes and produces messages, separate entry and exit connector flows are used for connecting the system to the message bus.

In some cases however, the consumption of a message also produces a message as the result. If these messages can be handled by asynchronous message flows but there is a need to somehow correlate them, use an <i>exit/entry connector</i>: this generates an <i>exit connector</i> that delivers messages to the consuming system, that also acts like an <i>entry connector</i> by placing messages produced by that same system back onto the message bus.

### 
The type of messages that are send back to the message bus by the <i>exit/entry connector</i>.

### 
The type of messages that are send to the connected system by the <i>exit/entry connector</i>, that result in the messages send back to the message bus handled by this offramp process.

### 
The web service operation name for this message type.

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
Normally, if a system consumes and produces messages, separate entry and exit connector flows are used for connecting the system to the message bus.

In some cases however, the consumption of a message also produces a message as the result. If these messages can be handled by asynchronous message flows but there is a need to somehow correlate them, use an <i>exit/entry connector</i>: this generates an <i>exit connector</i> that delivers messages to the consuming system, that also acts like an <i>entry connector</i> by placing messages produced by that same system back onto the message bus.

### 
The type of messages that are send back to the message bus by the <i>exit/entry connector</i>.

### 
The type of messages that are send to the connected system by the <i>exit/entry connector</i>, that result in the messages send back to the message bus handled by this offramp process.

