---
id: tcp-inbound-channel-adapter
title: TCP inbound channel adapter
sidebar_label: TCP inbound channel adapter
---
#### Defines an event-driven TCP/IP byte-message receiving adapter.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/ip.html#tcp-adapters" target="_blank">External documentation</a>


#### Connection factory
A <i>TCP connection factory</i> is needed by an inbound adapter.

If the connection factory has a type <i>server</i>, the factory is 'owned' by this adapter. 

If it has a type <i>client</i>, it is 'owned' by an outbound channel adapter and this adapter will receive any incoming messages on the connection created by the outbound adapter.

#### Error channel
If a (synchronous) downstream exception is thrown and an error channel is specified, the <code>MessagingException</code> will be sent to this channel. Otherwise, any such exception will simply be logged by the channel adapter.

#### Client mode
If set to <i>true</i>, causes the adapter to act as a client with respect to
 establishing the connection, rather than listening for incoming connections.

Requires a "client" connection factory, with <i>single-use</i> set to <i>false</i>.

Default is <i>false</i>.

#### Retry interval
When in client mode, specifies the retry interval (in milliseconds) if a connection
 cannot be established.

Default is <code>60000</code> (1 minute).

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

