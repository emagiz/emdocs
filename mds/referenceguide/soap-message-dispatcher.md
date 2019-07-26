---
id: soap-message-dispatcher
title: SOAP message dispatcher
sidebar_label: SOAP message dispatcher
---
#### Dispatches SOAP web service messages to registered endpoints.
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/server.html#message-dispatcher-servlet" target="_blank">External documentation</a>

SOAP-specific message dispatcher. 

Handles the message in the following order:

<b>1. Endpoint search</b> 
An appropriate endpoint is searched for using the configured Endpoint Mapping(s). If an endpoint is found, the invocation chain associated with the endpoint (preprocessors, postprocessors, and endpoints) will be executed in order to create a response.

<b>2. Adapter search</b> 
An appropriate adapter is searched for the endpoint. The Message Dispatcher delegates to this adapter to invoke the endpoint.

<b>3. Response</b> 
If a response is returned, it is sent on its way. If no response is returned (which could be due to a pre- or post-processor intercepting the request, for example, for security reasons), no response is sent. 

For more information about spring web services see:

<a href="http://static.springsource.org/spring-ws/sites/1.5/reference/html/server.html" target="_blank">Spring Webservices Reference 2.0</a>


The endpoint mapping is responsible for mapping incoming messages to appropriate endpoints.
 
An <i>endpoint mapping</i> delivers the endpoint that matches the incoming request, and may also deliver a list of <i>endpoint interceptors</i> that will be applied to the request and response.

The following types of mapping are available:
<b>1. Root element mapping</b>
The <i>Payload Root QName Endpoint Mapping</i> will use the qualified name of the root element of the request payload to determine the endpoint that handles it.


Specifies adapters that are used for delegating the dispatch of the message to an endpoint.
The dispatcher will look for an appropriate adapter after finding the endpoint in the mappings.

If not specified, the following endpoint adapters are used by default:
- <code>MessageEndpointAdapter</code>
- <code>PayloadEndpointAdapter</code>
- <code>MessageMethodEndpointAdapter</code>
- <code>PayloadMethodEndpointAdapter</code>
- <code>DefaultMethodEndpointAdapter</code>


Specifies classes that can resolve exceptions thrown during endpoint execution.
The dispatcher will try these resolvers (in order) to handle the exception, for example by converting it into a <i>SOAP Fault</i> response.

If not specified, the following endpoint exception resolvers are used by default:
- <code>SimpleSoapExceptionResolver</code>
- <code>SoapFaultAnnotationExceptionResolver</code>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

