---
id: http-inbound-gateway
title: HTTP inbound gateway
sidebar_label: HTTP inbound gateway
---
#### Gateway for receiving messages over HTTP and sending replies back.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/http.html#http-inbound" target="_blank">External documentation</a>

The HTTP inbound adapters need to be deployed within a servlet container. 

In sending a response to the client there are a number of ways to customize the behavior of the gateway. 
By default the gateway will simply acknowledge that the request was received by sending a <code>200</code> status code back. Customize this response by providing a <i>view name</i>. If you simply want to acknowledge the received HTTP request without sending a response message back, use a <i>HTTP inbound channel adapter</i> instead.

#### Supported methods
Comma-separated HTTP method names. Determines which types of request are allowed with this endpoint. Possible methods are: GET, POST, HEAD, OPTIONS, PUT, DELETE and TRACE.

Default is <code>POST, GET</code>.

#### Extract reply payload
Specify whether only the reply Message's payload should be passed in the response. 

If this is set to 'false', the entire Message will be used to generate the response. 

The default is 'true'. 

#### Mapped request headers
Comma-separated list of names of HTTP headers to be mapped from the HTTP request into the message headers. The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>). The string <code>HTTP_REQUEST_HEADERS</code> will match against any of the standard HTTP request headers.

All <a href="http://en.wikipedia.org/wiki/List_of_HTTP_header_fields" target="_blank">standard HTTP request headers</a> are mapped by default.

Note that all non-standard headers will automatically be prefixed with <code>X-</code>. This behaviour can be changed by using a custom <i>header mapper</i>.

#### Mapped response headers
Comma-separated list of names of m essage headers to be mapped into the HTTP headers of the HTTP response. The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>). The string <code>HTTP_RESPONSE_HEADERS</code> will match against any of the standard HTTP response headers.

All <a href="http://en.wikipedia.org/wiki/List_of_HTTP_header_fields" target="_blank">standard HTTP response headers</a> are mapped by default.

Note that all non-standard headers will automatically be prefixed with <code>X-</code>. This behaviour can be changed by using a custom <i>header mapper</i>.

#### Header mapper
A custom <code>HeaderMapper</code> implementation can be used to fully control the mapping between message headers and HTTP headers. For example, to configure whether to use the <code>X-</code> prefix for user-defined HTTP headers or not.

This setting is mutually exclusive with <i>mapped request headers</i> and <i>mapped response headers</i>.

#### Convert exceptions
In the case that a <i>view name</i> is not specified, this attribute can be used to override the default behaviour when there is a message handling exception (which is to rethrow).  If this flag is <code>true</code> then the normal conversion process will be applied to the exception and written out to the response body.

Default is <code>false</code>.

#### Payload expression
A SpEL expression that is evaluated in order to generate the message payload.

The evaluation context will be populated with an <code>org.springframework.http.HttpEntity</code> instance as the root object, and the following expression variables will also be made available:

<b>#requestParams</b> - a <code>MultiValueMap&lt;String, String&gt;</code> containing the request parameters from the query string or posted form data
<b>#pathVariables</b> - a <code>Map&lt;String, String&gt;</code> containing the URI path placeholders and their values
<b>#matrixVariables</b> - a <code>Map&lt;String, MultiValueMap&lt;String, String&gt;&gt;</code> containing the matrix variables according to <a href="http://docs.spring.io/spring/docs/current/spring-framework-reference/html/mvc.html#mvc-ann-matrix-variables" target="_blank">Spring MVC specification</a>
<b>#requestAttributes</b> - the <code>org.springframework.web.context.request.RequestAttributes</code> associated with the current request
<b>#requestHeaders</b> - the <code>org.springframework.http.HttpHeaders</code> object from the current request
<b>#cookies</b> - a <code>Map&lt;String, javax.servlet.http.Cookie&gt;</code> containing the cookies from the current request

<i>Optional</i>

#### Path
Allows you to specify the URI path (e.g. <code>/order/{orderId}</code>).

Any <code>{variable}</code> in this path will be available in the SpEL evaluation context as an entry in the <code>#pathVariables</code> map.

Ant-style path patterns are also supported (e.g. <code>/myPath/*.do</code>).

#### Request payload type
Target type for payload that is the conversion result of the request.

By default this value is <code>null</code> which means at runtime any "text" <i>Content-Type</i> will result in <code>java.lang.String</code> while all others default to <code>byte[]</code>.

#### Request timeout
Set the send timeout value for sending messages to the request channel.

Default is <code>1000</code> (1 second).

#### Reply timeout
Set the receive timeout value for receiving messages from the reply channel.

Default is <code>1000</code> (1 second).

#### Reply timeout status code expression
A SpEL expression that resolves to an <code>HttpStatus</code> code when rendering a response after a <i>reply timeout</i>. The expression must return an object which can be converted to a <code>org.springframework.http.HttpStatus</code> enum value. The evaluation context has a bean resolver but no variables, so the usage of this attribute is somewhat limited.

An example might be to resolve, at runtime, some scoped bean that returns an <code>HttpStatus</code> value, or use a literal expression e.g. <code>504</code>.

By default <i>reply timeout status code expression</i> is <code>null</code>, meaning that the default '500 Internal Server Error' response status will be returned after a timeout. When a timeout is not encountered, the <i>HTTP inbound gateway</i> resolves the status code from the <code>http_statusCode</code> header of the reply message.

#### View name
View name to be resolved when rendering a response.

#### Reply key
Specify the key to be used when adding the reply Message or payload to the model map, depending on the value of <i>Extract reply payload</i>.

Default when empty: <i>reply</i>

#### Errors key
In the case that a <i>view name</i> is specified this attribute can be used to
 override the default key of the errors (if the request cannot be handled).

Defaults to <code>errors</code> (similar to normal MVC usage).

#### Error code
In the case that a <i>view name</i> is specified this attribute can be used to override the default error code under which the handling exception is exposed.
 Defaults to <code>spring.integration.http.handler.error</code> and is supplied with 3 parameters: the exception itself, its message and its stack trace as a string.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this gateway's invocation. To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.


Custom message headers that will be added to request messages send by this gateway.

The value is determined by a SpEL expression, which has access to the body and headers of the incoming HTTP request, any path variables (as defined by the <i>path</i> property) and any query parameters from the request URL.

#### Request channel
Channel where request messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the request messages.

<i>Required</i>

#### Reply channel
Channel to consume the reply messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: http-inbound-gateway
title: HTTP inbound gateway
sidebar_label: HTTP inbound gateway
---

Gateway for receiving messages over HTTP and sending back replies.

In sending a response to the client there are a number of ways to customize the behavior of the gateway. If you simply want to acknowledge the received HTTP request without sending a response message back, use a <i>HTTP inbound channel adapter</i> instead.

To support this HTTP inbound endpoint, it needs to be deployed within a servlet container. The recommended way to do this is to use the <i>HTTP inbound endpoint dispatcher servlet</i> in a <i>Jetty server</i> support object.


Custom message headers that will be added to request messages send by this gateway.

The value is determined by a SpEL expression, which has access to the body and headers of the incoming HTTP request, any path variables (as defined by the <i>path</i> property) and any query parameters from the request URL.

