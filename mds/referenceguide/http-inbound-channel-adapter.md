---
id: http-inbound-channel-adapter
title: HTTP inbound channel adapter
sidebar_label: HTTP inbound channel adapter
---
#### Channel adapter for receiving messages over HTTP.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/http.html#http-inbound" target="_blank">External documentation</a>

The HTTP inbound adapters need to be deployed within a servlet container. 

This adapter will simply acknowledge that the request was received by sending a <code>200</code> status code back (or using the specified <i>MVC View</i> to generate a response). If you want to send a response message back, use a <i>HTTP inbound gateway</i> instead.

#### Supported methods
Comma-separated HTTP method names. Determines which types of request are allowed with this endpoint. Possible methods are: GET, POST, HEAD, OPTIONS, PUT, DELETE and TRACE.

Default is <code>POST, GET</code>.

#### Mapped request headers
Comma-separated list of names of HTTP headers to be mapped from the HTTP request into the message headers. The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>). The string <code>HTTP_REQUEST_HEADERS</code> will match against any of the standard HTTP request headers.

All <a href="http://en.wikipedia.org/wiki/List_of_HTTP_header_fields" target="_blank">standard HTTP request headers</a> are mapped by default.

Note that all non-standard headers will automatically be prefixed with <code>X-</code>. This behaviour can be changed by using a custom <i>header mapper</i>.

#### Header mapper
A custom <code>HeaderMapper</code> implementation can be used to fully control the mapping between message headers and HTTP headers. For example, to configure whether to use the <code>X-</code> prefix for user-defined HTTP headers or not.

This setting is mutually exclusive with <i>mapped request headers</i>.

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

#### Status code expression
A SpEL expression that resolves to an <code>HttpStatus</code> code when rendering a response. The expression must return an object which can be converted to a <code>org.springframework.http.HttpStatus</code> enum value. The evaluation context has a bean resolver but no variables, so the usage of this attribute is somewhat limited.

An example might be to resolve, at runtime, some scoped bean that returns an <code>HttpStatus</code> value, or use a literal expression e.g. <code>201</code>. For more control consider using an <i>HTTP inbound gateway</i>: it resolves the status code from the <code>http_statusCode</code> header of the reply message.

By default <i>status code expression</i> is <code>null</code>, meaning that the default '200 OK' response status will be returned.

#### Send timeout
Maximum amount of time in milliseconds to wait when sending a message to the channel if such channel may block. For example, a queue channel can block until space is available if its maximum capacity has been reached.

Default is <code>1000</code> (1 second).

#### View name
View name to be resolved when rendering a response.

#### Errors key
In the case that a <i>view name</i> is specified this attribute can be used to
 override the default key of the errors (if the request cannot be handled).

Defaults to <code>errors</code> (similar to normal MVC usage).

#### Error code
In the case that a <i>view name</i> is specified this attribute can be used to override the default error code under which the handling exception is exposed.
 Defaults to <code>spring.integration.http.handler.error</code> and is supplied with 3 parameters: the exception itself, its message and its stack trace as a string.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this gateway's invocation. To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.


Custom message headers that will be added to messages send by this adapter.

The value is determined by a SpEL expression, which has access to the body and headers of the incoming HTTP request, any path variables (as defined by the <i>path</i> property) and any query parameters from the request URL.

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: http-inbound-channel-adapter
title: HTTP inbound channel adapter
sidebar_label: HTTP inbound channel adapter
---

Channel adapter for receiving messages over HTTP.

This adapter will simply acknowledge that the request was received by sending a <code>200 OK</code> status code back (this can be customized to use other status codes). If you want to send a response message back, use a <i>HTTP inbound gateway</i> instead.

To support this HTTP inbound endpoint, it needs to be deployed within a servlet container. The recommended way to do this is to use the <i>HTTP inbound endpoint dispatcher servlet</i> in a <i>Jetty server</i> support object.


Custom message headers that will be added to messages send by this adapter.

The value is determined by a SpEL expression, which has access to the body and headers of the incoming HTTP request, any path variables (as defined by the <i>path</i> property) and any query parameters from the request URL.

