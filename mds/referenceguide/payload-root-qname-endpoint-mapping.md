---
id: payload-root-qname-endpoint-mapping
title: Payload root QName endpoint mapping
sidebar_label: Payload root QName endpoint mapping
---
#### Maps request messages to endpoints, based on the name of the root XML element.
Uses the <i> qualified name</i> of the root element of the webservice request payload to determine the endpoint that handles it. 

#### Default endpoint
The default endpoint to use, when this endpoint mapping does not result in a matching endpoint. 


The mappings between <i> qualified root names </i> and <i>endpoints</i>


Interceptors that will be applied <i>in the specified order</i> to the request and response message.

Available types:

<b>Payload validating interceptor</b>
Interceptor that validates the contents of web service messages using a schema. If not valid, the processing of the message will be stopped.

<b>HTTP request address extracting interceptor</b>
Interceptor that extracts the remote and local IP address and port from the incoming HTTP request, so these values can be used later in the message flow.

<b>WSS4J security interceptor</b>
Interceptor that can validate WS-Security information in requests and can secure the responses.

---
id: payload-root-qname-endpoint-mapping
title: Payload root QName endpoint mapping
sidebar_label: Payload root QName endpoint mapping
---
#### Maps request messages to endpoints, based on the name of the root XML element.
Uses the <i> qualified name</i> of the root element of the webservice request payload to determine the endpoint that handles it. 

#### Default endpoint
The default endpoint to use, when this endpoint mapping does not result in a matching endpoint. 


The mappings between <i> qualified root names </i> and <i>endpoints</i>


Interceptors that will be applied <i>in the specified order</i> to the request and response message.

Available types:

<b>Payload validating interceptor</b>
Interceptor that validates the contents of web service messages using a schema. If not valid, the processing of the message will be stopped.

<b>HTTP request address extracting interceptor</b>
Interceptor that extracts the remote and local IP address and port from the incoming HTTP request, so these values can be used later in the message flow.

<b>WSS4J security interceptor</b>
Interceptor that can validate WS-Security information in requests and can secure the responses.

