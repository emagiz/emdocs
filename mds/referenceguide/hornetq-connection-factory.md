---
id: hornetq-connection-factory
title: HornetQ connection factory
sidebar_label: HornetQ connection factory
---
#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Username
Optional username that is used for creating connections to the JMS server.

If not set (the default), the sending of user credentials is disabled.

#### Password
Optional password that is used for creating connections to the JMS server.

Must be provided if and only if the <i>username</i> property is also set.

#### High availability
Determines whether or not the connection should support high availability. <code>true</code> means it will connect to any available server in a cluster and support failover. 

The default value is <code>false</code>.


The initial set of servers used to make a connection to the cluster. Each one is tried in turn until a successful connection is made. Once a connection is made, the cluster topology is downloaded and the rest of the list is ignored.


<a href="http://docs.spring.io/spring/docs/3.1.x/spring-framework-reference/html/" target="_blank">External documentation</a>

#### Signature
Determines (together with the value for <i>XA</i>) the connection factory type that is used:

<b>Generic</b>: creates a <code>javax.jms.(XA)ConnectionFactory</code>
<b>Queue</b>: creates a <code>javax.jms.(XA)QueueConnectionFactory</code>
<b>Topic</b>: creates a <code>javax.jms.(XA)TopicConnectionFactory</code>

Default is <i>generic</i>.

#### XA
Determines (together with the value for <i>signature</i>) the connection factory type that is used:

<b>false</b>: creates a <code>javax.jms.(Queue/Topic)ConnectionFactory</code>
<b>true</b>: creates a <code>javax.jms.XA(Queue/Topic)ConnectionFactory</code>

Default is <i>false</i>.

#### Connection load balancing policy class name
The name of the load balancing class.

Default is 'org.hornetq.api.core.client.loadbalance.RoundRobinConnectionLoadBalancingPolicy'.

#### Client ID
The pre-configured client ID for the connection factory.

This represents the client id for a JMS client and is needed for creating durable subscriptions. Any connection created by this connection factory will have this set as its client id.

Default is 'empty'.

#### Initial message packet size
Sets the initial size of messages created through this factory. Value must be greater than 0.

Default is '1500'.


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#message-grouping" target="_blank">External documentation</a>

#### Auto group
Whether or not message grouping is automatically used.

Default is 'false'.

#### Group ID
Sets the group ID that will be set on each message sent through this factory.


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#large-messages" target="_blank">External documentation</a>

#### Cache large messages client
If <code>true</code> clients using this connection factory will hold the large message body on temporary files.

Default is <code>false</code>.

#### Min large message size
The size (in bytes) before a message is treated as large. Large messages will be split up and sent in fragments.

Default is <code>102400</code> (100 KiB).

Be aware that you should not use values here that are bigger than the JMS server's <i>journal buffer size</i>, which is <code>501760</code> (490 KiB) by default.

#### Compress large messages
Whether to compress large messages.

Default is <code>false</code>.


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#connection-ttl" target="_blank">External documentation</a>

#### Client failure check period
The period (in ms) after which the client will consider the connection failed after not receiving packets from the server.

Default is '5000' (5 seconds).

#### Connection TTL
The time to live (in ms) for connections.

The TTL determines how long the server will keep a connection alive in the absence of any data arriving from the client. The client will automatically send "ping" packets periodically to prevent the server from closing it down. If the server doesn't receive any packets on a connection for the connection TTL time, then it will automatically close all the sessions on the server that relate to that connection.

Default is '60000' (1 minute).

#### Call timeout
The timeout (in ms) for remote calls.

Default is '30000' (30 seconds).

#### Call failover timeout
Similar to <i>call timeout</i> but used when a call is made during a failover attempt. 

Default is <code>-1</code> (no timeout).


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#flow-control" target="_blank">External documentation</a>

#### Consumer max rate
The fastest rate a consumer may consume messages per second.

Default is <code>-1</code>, i.e. no limit.

#### Consumer window size
By default, consumers buffer messages from the server in a client side buffer before the client consumes them. This improves performance: otherwise a network round trip would be involved for every message, which considerably reduces performance.

Setting the <i>consumer window size</i> correctly can considerably improve performance depending on the messaging use case. As an example, let's consider the two extremes:

<b>Fast consumers</b>
Fast consumers can process messages as fast as they consume them (or even faster). To allow fast consumers, set the <i>consumer window size</i> to <code>-1</code>. This will allow unbounded message buffering on the client side. Use this setting with caution: it can overflow the client memory if the consumer is not able to process messages as fast as it receives them.

<b>Slow consumers</b>
Slow consumers takes significant time to process each message and it is desirable to prevent buffering messages on the client side so that they can be delivered to another consumer instead. Consider a situation where a queue has 2 consumers; 1 of which is very slow. Messages are delivered in a round robin fashion to both consumers, the fast consumer processes all of its messages very quickly until its buffer is empty. At this point there are still messages awaiting to be processed in the buffer of the slow consumer thus preventing them being processed by the fast consumer. The fast consumer is therefore sitting idle when it could be processing the other messages. To allow slow consumers, set the <i>consumer window size</i> to <code>0</code> (for no buffer at all). This will prevent the slow consumer from buffering any messages on the client side. Messages will remain on the server side ready to be consumed by other consumers.

Most of the consumers cannot be clearly identified as fast or slow consumers but are in-between. In that case, setting the value of <i>consumer window size</i> to optimize performance depends on the messaging use case and requires benchmarks to find the optimal value, but a value of 1 MiB is fine in most cases.

Default is <code>1048576</code> (1 MiB).

#### Producer max rate
The maximum rate of messages per second that can be sent.

Default is <code>-1</code>, i.e. no limit.

#### Producer window size
The window size in bytes for producers sending messages.

Default is 65536 (64 KiB).

#### Confirmation window size
The window size (in bytes) for re-attachment confirmations.

Default is <code>-1</code>, which disables buffering and prevents re-attachment from occurring, forcing reconnect instead.

To enable transparent session re-attachment, enter a positive value, e.g. <code>1048576</code> (1 MiB).


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#send-guarantees" target="_blank">External documentation</a>

#### Block on acknowledge
Whether or not messages are acknowledged synchronously.

If this is set to true then all calls to acknowledge on non transacted sessions will block until the acknowledge has reached the server, and a response has been sent back. You might want to set this to true if you want to implement a strict at most once delivery policy. 

Default is 'false'.

#### Block on non durable send
Whether or not non-durable messages are sent synchronously.

If this is set to true then all calls to send for non-durable messages on non transacted sessions will block until the message has reached the server, and a response has been sent back. 

Default is 'false'.

#### Block on durable send
Whether or not durable messages are sent synchronously.

If this is set to true then all calls to send for durable messages on non transacted sessions will block until the message has reached the server, and a response has been sent back.

Default is 'true'.

#### Dups OK batch size
The batch size (in bytes) between acknowledgements when using DUPS_OK_ACKNOWLEDGE mode.

When the JMS acknowledge mode is set to DUPS_OK it is possible to configure the consumer so that it sends acknowledgements in batches rather that one at a time, saving valuable bandwidth. 

Default is 1048576 (1 MiB).

#### Transaction batch size
The batch size (in bytes) between acknowledgements when using a transactional session.

When receiving messages in a transaction it makes it possible to configure the consumer to send acknowledgements in batches rather than individually saving valuable bandwidth.

Default is 1048576 (1 MiB).


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#pre-acknowledge" target="_blank">External documentation</a>

#### Pre-acknowledge
Whether messages are pre acknowledged by the server before sending.

Default is 'false'.


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#client-reconnection" target="_blank">External documentation</a>

#### Retry interval
The time (in ms) to retry a connection after failing.

Default is <code>2000</code> (2 seconds).

#### Max retry interval
The maximum retry interval in the case a retry-interval-multiplier has been specified.

Default is <code>2000</code> (2 seconds).

#### Retry interval multiplier
Multiplier to apply to successive retry intervals.

Default is '1.0'.

#### Reconnect attempts
Maximum number of retry attempts, '-1' signifies infinite.

Default is '0'.


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#failover" target="_blank">External documentation</a>

#### Initial connect attempts
Since the client doesn't learn about the full topology until after the first connection is made there is a window where it doesn't know about the backup. If a failure happens at this point the client can only try reconnecting to the original live server. This property configures how many attempts the client will make: once this number of attempts has been made without success an exception will be thrown.

Default is <code>1</code>.

#### Failover on initial connection
Whether or not to failover to backup on event that initial connection to live server fails.

Default is <code>false</code>.


<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#thread-pooling.client.side" target="_blank">External documentation</a>

#### Use global pools
Whether or not to use a global thread pool for threads.

Default is 'true'.

#### Scheduled thread pool max size
The size of the scheduled thread pool.

Default is '5'.

#### Thread pool max size
The size of the thread pool.

Default is '-1'.

