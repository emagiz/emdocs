---
id: http-outbound-channel-adapter
title: HTTP outbound channel adapter
sidebar_label: HTTP outbound channel adapter
---
#### Used to send (unidirectional) HTTP messages.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/http.html#http-outbound" target="_blank">External documentation</a>

An adapter that sends HTTP requests in a unidirectional way. This means that a successful HTTP response will simply execute without sending any messages to a reply channel. In the case of any non-successful HTTP response status code, it will throw an exception.

If you <i>are</i> interested in the contents of the response message, use a <i>HTTP outbound gateway</i> instead.

#### URL
URL to which the requests should be sent. It may include <code>{placeholders}</code> for evaluation against <i>URI variables</i>.

#### HTTP method
The HTTP method to use when executing requests with this gateway.

Default is <code>POST</code>.

#### Expected response type
The expected type to which the response body should be converted. Default is <code>org.springframework.http.ResponseEntity</code>.

To take advantage of the HTTP message converters registered on this gateway provide a different type, for example <code>java.lang.String</code>.


Expression to be evaluated against the message to replace a URI <code>{placeholder}</code> with the evaluation result.

#### URL expression
SpEL expression resolving to a URL to which the requests should be sent. The resolved value may include <code>{placeholders}</code> for further evaluation against <i>URI variables</i>.

<i>Optional</i> ; mutually exclusive with <i>URL</i>.

#### Encode URI
When set to <code>false</code>, the real URI won't be encoded before the request is sent. This may be useful in some scenarios as it allows user control over the encoding, if needed, for example by using the <i>URL expression</i>.

Default is <code>true</code>.

#### HTTP method expression
SpEL expression to dynamically determine the HTTP method (<code>POST</code>, <code>GET</code>, etc) to use when executing requests with this adapter.

<i>Optional</i> ; mutually exclusive with <i>HTTP method</i>.

<b>Note that the standard JDK HTTP library does not support the HTTP <code>PATCH</code> method.</b> Use a custom <i>REST template</i> support object configured with the <i>Apache HttpComponents</i> request factory to enable <code>PATCH</code>.

#### Expected response type expression
SpEL expression to determine the type for the expected response to which the response body should be converted. The returned value of the expression could be an instance of <code>java.lang.Class</code> or <code>java.lang.String</code> representing a fully qualified class name.

<i>Optional</i> ; mutually exclusive with <i>expected response type</i>.

#### Extract payload
Specify whether the outbound message's payload should be extracted when preparing the request body; otherwise the message itself will be serialized.

Default value is <code>true</code>.

#### Mapped request headers
Comma-separated list of names of message headers to be mapped into the HTTP headers of the HTTP request. The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>). The string <code>HTTP_REQUEST_HEADERS</code> will match against any of the standard HTTP request headers.

All <a href="http://en.wikipedia.org/wiki/List_of_HTTP_header_fields" target="_blank">standard HTTP request headers</a> are mapped by default.

Note that all non-standard headers will automatically be prefixed with <code>X-</code>. This behaviour can be changed by using a custom <i>header mapper</i>.

#### Header mapper
A custom <code>HeaderMapper</code> implementation can be used to fully control the mapping between message headers and HTTP headers. For example, to configure whether to use the <code>X-</code> prefix for user-defined HTTP headers or not.

This setting is mutually exclusive with <i>mapped request headers</i>.

#### Charset
Specify the charset name to use for converting string-typed payloads to bytes.

Default is <code>UTF-8</code>.

#### REST template
Allows for specifying a custom <code>RestTemplate</code>.

A REST template provides a configurable extension point for communicating with HTTP servers using RESTful principles. This can be used to add authentication to HTTP connections, for example.

#### Channel
Channel to consume messages from.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

