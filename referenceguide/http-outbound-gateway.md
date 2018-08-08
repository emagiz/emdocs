
Used to send HTTP requests and receive HTTP response messages.
A gateway that sends HTTP requests based on incoming messages, and converts the HTTP response (which might just be a HTTP status code) to the result message.

If you're not interested in the response message, use a <i>HTTP outbound channel adapter</i> instead.

This gateway dynamically determines the <code>Content-Type</code> for the outgoing HTTP request using these rules:
1) If present, the value of the <code>contentType</code> message header is used
2) If the HTTP method is one of <code>GET, HEAD, TRACE</code>, the content type is not applicable (these methods do not use a request body)
3) If the message payload is a <code>String</code>, the content type will be <code>text/plain</code>
4) If the message payload is a <code>byte[]</code>, the content type will be <code>application/octet-stream</code>
5) If the message payload is a <code>javax.xml.transform.Source</code>, the content type will be <code>text/xml</code>
6) If the message payload is a <code>Map&lt;String, String&gt;</code>, the content type will be <code>application/x-www-form-urlencoded</code>
7) If the message payload is a <code>Map&lt;String, ?&gt;</code>, the content type will be <code>multipart/form-data</code> (note: because of rule 6, this means at least one value in the map must be a type other than <code>String</code>)
8) If none of the above, the content type will be <code>application/x-java-serialized-object</code>

Supported payload types when filling the body of the HTTP request message include:
- <code>byte[]</code>: these are simply copied to the body
- <code>String</code>: these are converted to bytes using the specified <i>charset</i> and written to the body
- <code>javax.xml.transform.Source</code>: these are written to the body using the <i>identity transform</i>
- <code>Map&lt;String, ?&gt;</code>: these are written as form data to the body, using either the <code>multipart/form-data</code> format (if so specified by the <code>Content-Type</code>) or the <code>application/x-www-form-urlencoded</code> format otherwise

Note that while rules 3-7 nicely match the supported payload types, by using rule 1 you can create <i>any</i> content type. However, this also allows you to create invalid combinations if you don't correctly match it to the payload type.


URL expression
SpEL expression resolving to a URL to which the requests should be sent. The resolved value may include <code>{placeholders}</code> for further evaluation against <i>URI variables</i>.

<i>Optional</i> ; mutually exclusive with <i>URL</i>.


Encode URI
When set to <code>false</code>, the real URI won't be encoded before the request is sent. This may be useful in some scenarios as it allows user control over the encoding, if needed, for example by using the <i>URL expression</i>.

Default is <code>true</code>.


HTTP method expression
SpEL expression to dynamically determine the HTTP method (<code>POST</code>, <code>GET</code>, etc) to use when executing requests with this adapter.

<i>Optional</i> ; mutually exclusive with <i>HTTP method</i>.

<b>Note that the standard JDK HTTP library does not support the HTTP <code>PATCH</code> method.</b> Use a custom <i>REST template</i> support object configured with the <i>Apache HttpComponents</i> request factory to enable <code>PATCH</code>.


Expected response type expression
SpEL expression to determine the type for the expected response to which the response body should be converted. The returned value of the expression could be an instance of <code>java.lang.Class</code> or <code>java.lang.String</code> representing a fully qualified class name.

<i>Optional</i> ; mutually exclusive with <i>expected response type</i>.


Extract request payload
Specify whether the outbound message's payload should be extracted when preparing the request body; otherwise the message itself will be serialized.

Default value is <code>true</code>.


Mapped request headers
Comma-separated list of names of message headers to be mapped into the HTTP headers of the HTTP request. The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>). The string <code>HTTP_REQUEST_HEADERS</code> will match against any of the standard HTTP request headers.

All <a href="http://en.wikipedia.org/wiki/List_of_HTTP_header_fields" target="_blank">standard HTTP request headers</a> are mapped by default.

Note that all non-standard headers will automatically be prefixed with <code>X-</code>. This behaviour can be changed by using a custom <i>header mapper</i>. Also note that the <code>contentType</code> message header is mapped to the standard HTTP header <code>Content-Type</code>.


Mapped response headers
Comma-separated list of names of HTTP headers to be mapped from the HTTP response into the message headers. The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>). The string <code>HTTP_RESPONSE_HEADERS</code> will match against any of the standard HTTP response headers.

All <a href="http://en.wikipedia.org/wiki/List_of_HTTP_header_fields" target="_blank">standard HTTP response headers</a> are mapped by default.

Note that all non-standard headers will automatically be prefixed with <code>X-</code>. This behaviour can be changed by using a custom <i>header mapper</i>. Also note that the standard HTTP header <code>Content-Type</code> is mapped to the <code>contentType</code> message header.

Be aware that independently from this setting, the <code>http_statusCode</code> message header will <i>always</i> be present on the reply message. This message header &ndash; together with other special headers such as <code>Accept</code>, <code>Access-Control-Allow-Methods</code>, <code>Access-Control-Request-Method</code>, <code>Allow</code>, <code>Content-Type</code>, and <code>Range</code> &ndash; can cause problems when left on the reply message. To prevent these issues you might want to <i>not</i> map any response headers at all, or only explicitly map the ones you are actually interested in. Remember that you still might have to remove the <code>http_statusCode</code> message header: the <i>header filter</i> transformer makes this really easy.


Header mapper
A custom <code>HeaderMapper</code> implementation can be used to fully control the mapping between message headers and HTTP headers. For example, to configure whether to use the <code>X-</code> prefix for user-defined HTTP headers or not.

This setting is mutually exclusive with <i>mapped request headers</i> and <i>mapped response headers</i>.


Charset
Specify the charset name to use for converting string-typed payloads to bytes.

Default is <code>UTF-8</code>.


Reply timeout
Allows you to specify how long (in milliseconds) this gateway will wait for the reply message to be sent successfully to the reply channel before throwing an exception. This attribute only applies when the channel might block, for example when using a bounded queue channel that is currently full.

Also, keep in mind that when sending to a <i>direct channel</i>, the invocation will occur in the sender's thread. Therefore, the failing of the send operation may be caused by other components further downstream.

If not specified, by default the gateway will wait indefinitely.


Transfer cookies
When set to <code>true</code>, if a response contains a HTTP <i>Set-Cookie</i> header, it will be mapped to a <i>Cookie</i> message header. This enables simple cookie handling where subsequent HTTP interactions in the same message flow can use a cookie supplied by the server.

Default is <code>false</code>.


REST template
Allows for specifying a custom <code>RestTemplate</code>.

A REST template provides a configurable extension point for communicating with HTTP servers using RESTful principles. This can be used to add authentication to HTTP connections, for example.


URL
URL to which the requests should be sent. It may include <code>{placeholders}</code>.

<i>Required</i>


HTTP method
The HTTP method to use when executing requests with this gateway.

Default is <code>POST</code>.


Expected response type
The expected type to which the response body should be converted. Default is <code>org.springframework.http.ResponseEntity</code>.

To take advantage of the HTTP message converters registered on this gateway provide a different type, for example <code>java.lang.String</code>.


Expression to be evaluated against the message to replace a URI <code>{placeholder}</code> with the evaluation result.


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.


Id
Name that uniquely identifies this flow component.

<i>Required</i>


Request channel
Channel to consume the request messages from.

<i>Required</i>


Reply channel
Channel where reply messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the reply messages.

<i>Required</i>

