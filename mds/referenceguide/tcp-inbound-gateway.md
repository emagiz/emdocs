---
id: tcp-inbound-gateway
title: TCP inbound gateway
sidebar_label: TCP inbound gateway
---
#### Used to receive TCP/IP byte-messages and send reply messages.
<a href="http://static.springsource.org/spring-integration/docs/2.1.x/reference/html/ip.html#tcp-gateways" target="_blank">External documentation</a>


#### Connection factory
A <i>TCP connection factory</i> is needed by an inbound gateway. The connection factory must be of type <i>server</i>.

#### Reply timeout
The timeout value (in milliseconds) for receiving reply messages.

Default is <code>1000</code> (one second).

#### Error channel
If a (synchronous) downstream exception is thrown and an error channel is specified, the <code>MessagingException</code> will be sent to this channel and the ultimate response of the error flow will be returned as a response by the gateway.

If no error channel is specified, any such exception will simply be logged by the gateway. In such a situation, no response is sent to the client. 

#### Client mode
If set to <i>true</i>, causes the gateway to act as a client with respect to
 establishing the connection, rather than listening for incoming connections.

Requires a "client" connection factory, with <i>single-use</i> set to <i>false</i>.

Default is <i>false</i>.

#### Retry interval
When in client mode, specifies the retry interval (in milliseconds) if a connection
 cannot be established.

Default is <code>60000</code> (1 minute).

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

