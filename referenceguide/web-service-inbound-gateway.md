# Web service inbound gateway
#### Used to receive webservice calls and send reply messages.
Gateway to receive SOAP web service calls over HTTP(S) and send SOAP reply messages. This is used in combination with a servlet container, e.g. <i>Jetty Server</i>, where you have to specify which web service operations are forwarded to this gateway.

Both the request and the response messages are plain XML, as this gateway will automatically unwrap and wrap the SOAP message. The default error handling will result in a <i>SOAP Fault</i> being send back to the caller in case of an exception in the message flow.

When developing or debugging a web service, it can be quite useful to look at the content of a (SOAP) message when it arrives, or just before it is sent. If you have access to the eMagiz OSGi runtime, you can do this by using the following console commands:
<code>log:set TRACE org.springframework.ws.server.MessageTracing.received</code>
and/or
<code>log:set TRACE org.springframework.ws.server.MessageTracing.sent</code>

Alternatively, you can add the following lines to the <code>etc/org.ops4j.pax.logging.cfg</code> config file (no restart required):
<code>log4j.logger.org.springframework.ws.server.MessageTracing.received = TRACE</code>
and/or
<code>log4j.logger.org.springframework.ws.server.MessageTracing.sent = TRACE</code>

Both methods will cause the (SOAP) requests and responses to be written to the log file. Don't forget to change log levels back to INFO, as TRACE has negative performance impact and can <b>seriously compromise security</b>!

#### Extract payload
Set to false to forward the entire <i>Web Service Message</i> instead of just its payload as a Message to the request channel. 

This might be useful, for example, when a custom <i>Transformer</i> works against the <i>Web Service Message</i> directly. 

#### Error channel
The channel that error messages will be sent to if a failure occurs in this gateway's invocation. To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.

#### Reply timeout
Maximum time in milliseconds to wait for a reply from the downstream message flow initiated by this gateway.


This attribute is only relevant if at least some part of the downstream flow is asynchronous.

#### Mapped request headers
Comma-separated list of names of SOAP headers to be mapped from the SOAP request into the message headers.

The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>).

Cannot be used in combination with a <i>header mapper</i>.

#### Mapped reply headers
Comma-separated list of names of message headers to be mapped into the SOAP headers of the SOAP reply.

The values in this list can also be simple patterns to be matched against the header names (e.g. <code>foo*</code> or <code>*foo</code>).

Cannot be used in combination with a <i>header mapper</i>.

#### Header mapper
A SOAP header mapper that this gateway will use to map between Spring Integration message headers and the SOAP message.

Cannot be used in combination with <i>mapped request headers</i> or <i>mapped reply headers</i>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Request channel
Channel where request messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the request messages.

<i>Required</i>

#### Reply channel
Channel to consume the reply messages from.

<i>Required</i>

