---
id: web-service-outbound-gateway
title: Web service outbound gateway
sidebar_label: Web service outbound gateway
---
#### Used to request webservice calls and receive reply messages.
A gateway that sends SOAP requests over HTTP(S) based on incoming messages, and converts the SOAP response to the result message.

Both the request and the response messages should be plain XML, as this gateway will automatically wrap and unwrap them with the required SOAP elements. Responses containing a <i>SOAP Fault</i> are automatically converted to a <code>SoapFaultClientException</code>, thereby triggering the flow's error handling.

When developing or debugging a web service, it can be quite useful to look at the content of a (SOAP) message when it arrives, or just before it is sent. If you have access to the eMagiz OSGi runtime, you can do this by using the following console commands:
<code>log:set TRACE org.springframework.ws.client.MessageTracing.sent</code>
and/or
<code>log:set TRACE org.springframework.ws.client.MessageTracing.received</code>

Alternatively, you can add the following lines to the <code>etc/org.ops4j.pax.logging.cfg</code> config file (no restart required):
<code>log4j.logger.org.springframework.ws.client.MessageTracing.sent = TRACE</code>
and/or
<code>log4j.logger.org.springframework.ws.client.MessageTracing.received = TRACE</code>

Both methods will cause the (SOAP) requests and responses to be written to the log file. Don't forget to change log levels back to INFO, as TRACE has negative performance impact and can <b>seriously compromise security</b>!

#### URI
The destination URI for this web service gateway.

This URI may include <code>{placeholders}</code> whose values are determined by evaluating SpEL expressions provided via <i>uri-variable</i> sub-elements. The root object for those evaluations is the actual request message at runtime, i.e. you can access its payload or headers in the expression.

#### Requires reply
Specify whether this outbound gateway must return a non-<code>null</code> value, i.e. whether every request message must result in a reply message.

If <code>true</code>, a <code>ReplyRequiredException</code> will be thrown when the underlying service returns a <code>null</code> value or an empty string (if <i>ignore empty responses</i> is <code>true</code>).

Default is <code>false</code>.

#### Ignore empty responses
Indicates whether empty string response payloads should be considered as <i>null</i>. See also <i>requires reply</i>.

Note that when <i>requires reply</i> is <code>true</code> the response is not actually "ignored", because it will cause a <code>ReplyRequiredException</code> to be thrown. Set this to <code>false</code> if you want to send empty string responses in reply messages.

Default is <code>true</code>.

#### Message factory
Specifies the web service message factory responsible for creating the request messages and parsing the response messages.

If not specified, a <code>SaajSoapMessageFactory</code> for SOAP version 1.1 will be used.

#### Message sender
Sets the single message sender used for sending messages. 

This message sender will be used to resolve an URI to a WebServiceConnection.

By default, a <i>HttpUrlConnectionMessageSender</i> is used: this <i>WebServiceMessageSender</i> implementation uses standard J2SE facilities to execute POST requests, without support for HTTP authentication or advanced configuration options. It is designed for easy subclassing, customizing specific template methods. However, consider <i>HttpComponentsMessageSender</i> for more sophisticated needs: the J2SE <i>HttpURLConnection</i> is rather limited in its capabilities.

#### Interceptor
Interceptor that will be applied to the request and the response. An intercepter can manipulate the request or the response before and after the processing of the message by the gateway.

These can be extremely useful when you want to apply specific functionality to certain requests, for example, dealing with security-related SOAP headers, or the logging of request and response messages.

Some of the security-related interceptor implementations and their specific functionality are:

<b>Mendix authentication SAAJ SOAP interceptor</b>
Adds <i>Mendix</i> specific authentication SOAP headers to request messages, containing a username and password.

<b>Metacom authentication SAAJ SOAP interceptor</b>
Adds a <i>Metacom</i> specific session ID token to the SOAP body of the request message. The session ID tokens are acquired by sending a username and password to the <i>Metacom</i> login system.

<b>Zimbra authentication SAAJ SOAP interceptor</b>
Adds <i>Zimbra</i> specific authentication token SOAP headers to request messages. The authentication tokens are acquired by sending a username and password to the <i>Zimbra</i> authentication system.

<b>WSS4J security interceptor</b>
Interceptor based on <a href="http://ws.apache.org/wss4j/" target="_blank">Apache's WSS4J</a> that adds <i>WS-Security</i> aspects (authentication, XML digital signatures, XML encryption and decryption) to the web service. Implements the following <i>OASIS Web Services Security</i> standards:
- <a href="http://docs.oasis-open.org/wss/v1.1/wss-v1.1-spec-os-SOAPMessageSecurity.pdf" target="_blank">SOAP Message Security 1.1</a>
- <a href="http://docs.oasis-open.org/wss/v1.1/wss-v1.1-spec-os-UsernameTokenProfile.pdf" target="_blank">Username Token Profile 1.1</a>
- <a href="http://docs.oasis-open.org/wss/v1.1/wss-v1.1-spec-os-x509TokenProfile.pdf" target="_blank">X.509 Certificate Token Profile 1.1</a>
- <a href="http://docs.oasis-open.org/wss/v1.1/wss-v1.1-spec-os-SAMLTokenProfile.pdf" target="_blank">SAML Token Profile 1.1</a>
- <a href="http://docs.oasis-open.org/wss/v1.1/wss-v1.1-spec-os-KerberosTokenProfile.pdf" target="_blank">Kerberos Token Profile 1.1</a>
- <a href="http://www.ws-i.org/Profiles/BasicSecurityProfile-1.1.html" target="_blank">Basic Security Profile 1.1</a>

#### Request callback
Callback that will be applied to the request. A web service request callback can change the request message after the payload has been written to it but prior to invocation of the actual web service (and before any interceptors are applied).

<b>SOAP action callback</b>
Adds a <code>SOAPAction</code> HTTP header to the request message.

<b>WS-Addressing action callback</b>
Adds a <code>wsa:Action</code> SOAP header to the request message.

#### Fault message resolver
Specifies the fault message resolver responsible for handling faults when calling the web service.

If not specified, a <i>SOAP fault message resolver</i> will be used: this fault resolver simply throws a <code>SoapFaultClientException</code> when a fault occurs. The message of this exception only contains the <code>&lt;faultstring&gt;</code> of the SOAP Fault.

You can also choose to use a <i>detailed SOAP fault message resolver</i> instead: this fault resolver throws a <code>SoapFaultException</code> when a fault occurs. The message of this exception includes the <code>&lt;faultcode&gt;</code>, <code>&lt;faultstring&gt;</code> and <code>&lt;detail&gt;</code> of the SOAP Fault.

#### Mapped request headers
Comma-separated list of names of message headers to be mapped into the SOAP headers of the SOAP request.

The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>).

Cannot be used in combination with a <i>header mapper</i>.

#### Mapped reply headers
Comma-separated list of names of SOAP headers to be mapped from the SOAP reply into the message headers.

#### Header mapper
A SOAP header mapper that this gateway will use to map between Spring Integration message headers and the SOAP message.

Cannot be used in combination with <i>mapped request headers</i> or <i>mapped reply headers</i>.

#### Reply timeout
Allows you to specify how long (in milliseconds) this gateway will wait for the reply message to be sent successfully to the reply channel before throwing an exception. This attribute only applies when the channel might block, for example when using a bounded queue channel that is currently full.

Also, keep in mind that when sending to a <i>direct channel</i>, the invocation will occur in the sender's thread. Therefore, the failing of the send operation may be caused by other components further downstream.

If not specified, by default the gateway will wait indefinitely.

#### Encode URI
When set to <code>false</code>, the URI won't be encoded before the request is sent. This may be useful in some scenarios as it allows user control over the encoding, if needed.

Default is <code>true</code>.


Expression to be evaluated against the message to replace a URI <code>{placeholder}</code> with the evaluation result.

#### Request channel
Channel to consume the request messages from.

<i>Required</i>

#### Reply channel
Channel where reply messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the reply messages.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

