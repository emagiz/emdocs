# JMS inbound gateway
#### Receives JMS request messages from a connection and sends JMS reply messages.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/jms.html#jms-inbound-gateway" target="_blank">Documentation</a>

Receives JMS request messages from the specified request destination at the connection created by the <i>connection factory</i>, and sends JMS reply messages to the specified reply destination using the same <i>connection factory</i>.

#### Selector
A JMS message selector boolean expression that evaluates the headers of the messages. Only the messages where this expression evaluates to <code>true</code> are received.

See the java JMS specification for message selector syntax:
<a href="http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html" target="_blank">http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html</a>

#### Correlation key
Provide the name of a JMS property that should be copied from the request message to the reply message.

If <b>no</b> value is provided for this attribute then the <i>JMSMessageID</i> from the request will be copied into the <i>JMSCorrelationID</i> of the reply, unless there is already a value in the <i>JMSCorrelationID</i> property of the newly created reply message in which case nothing will be copied.

If the <i>JMSCorrelationID</i> of the request message should be copied into the <i>JMSCorrelationID</i> of the reply message instead, then this value should be set to <code>"JMSCorrelationID"</code>. Any other value will be treated as a JMS string property to be copied as-is from the request message into the reply message with the same property name.

#### Subscription durable
Boolean property indicating whether to make the subscription durable. The durable subscription name to be used can be specified through the <i>subscription name</i> property. Default is <i>false</i>.

Set this to <i>true</i> to register a durable subscription, typically in combination with a <i>subscription name</i> value (unless your message listener class name is good enough as subscription name).

#### Subscription shared
Boolean property indicating whether to make the subscription shared. The shared subscription name to be used can be specified through the <i>subscription name</i> attribute. Default is <code>false</code>.

Set this to <code>true</code> to register a shared subscription, typically in combination with a <i>subscription name</i> value (unless your message listener class name is good enough as subscription name).

Note that shared subscriptions may also be durable, so this flag can (and often will) be combined with <i>subscription durable</i> as well. Requires a JMS 2.0 compatible message broker.

#### Subscription name
The name of a subscription to create. To be applied in case of a topic (pub-sub domain) with a shared or durable subscription. The subscription name needs to be unique within this client's JMS client id. Default is the class name of the specified message listener.

Note: Only 1 concurrent consumer (which is the default of the message listener container) is allowed for each subscription, except for a shared subscription (which requires JMS 2.0).

#### Client id
The JMS client id for a shared connection created and used by this container.

Note that client ids need to be unique among all active connections of the underlying JMS provider. Furthermore, a client id can only be assigned if the original connection factory hasn't already assigned one.

#### Concurrent consumers
Specify the number of concurrent consumers to create.

Default is <code>1</code>.

Specifying a higher value for this setting will increase the standard level of scheduled concurrent consumers at runtime: This is effectively the minimum number of concurrent consumers which will be scheduled at any given time. This is a static setting; for dynamic scaling, consider specifying the <i>max concurrent consumers</i> setting instead.

<b>Do not raise the number of concurrent consumers for a topic, unless vendor-specific setup measures clearly allow for it.</b> With regular setup, this would lead to concurrent consumption of the same message, which is hardly ever desirable.

Note that when increasing this number, you'll probably also want to disable any consumer buffering of messages (HornetQ calls this <i>consumer window size</i>) on the JMS connection factory.

#### Max. concurrent consumers
Specify the maximum number of concurrent consumers to create.

Default is <code>1</code>.

If this setting is higher than <i>concurrent consumers</i>, the listener container will dynamically schedule new consumers at runtime, provided that enough incoming messages are encountered. Once the load goes down again, the number of consumers will be reduced to the standard level again.

Raising the number of concurrent consumers is recommendable in order to scale the consumption of messages coming in from a queue. However, note that any ordering guarantees are lost once multiple consumers are registered. In general, stick with 1 consumer for low-volume queues.

<b>Do not raise the number of concurrent consumers for a topic, unless vendor-specific setup measures clearly allow for it.</b> With regular setup, this would lead to concurrent consumption of the same message, which is hardly ever desirable.

Note that when increasing this number, you'll probably also want to disable any consumer buffering of messages (HornetQ calls this <i>consumer window size</i>) on the JMS connection factory.

#### Cache level
Specify the level of caching that this listener container is allowed to apply.
Default is <code>CACHE_NONE</code> if an external transaction manager has been specified (to reobtain all resources freshly within the scope of the external transaction), and <code>CACHE_CONSUMER</code> otherwise (operating with local JMS resources).

Some J2EE servers only register their JMS resources with an ongoing XA transaction in case of a freshly obtained JMS Connection and Session, which is why this listener container by default does not cache any of those. However, if you want to optimize for a specific server, consider switching this setting to at least <code>CACHE_CONNECTION</code> or <code>CACHE_SESSION</code> even in conjunction with an external transaction manager.

Currently known servers that absolutely require <code>CACHE_NONE</code> for XA transaction processing: JBoss 4. For any others, consider raising the cache level.

Possible cache level values:
<b>0</b>: <code>CACHE_NONE</code>
<b>1</b>: <code>CACHE_CONNECTION</code>
<b>2</b>: <code>CACHE_SESSION</code>
<b>3</b>: <code>CACHE_CONSUMER</code>

#### Max. messages per task
Specify the maximum number of messages to process in one task. More concretely, this limits the number of message reception attempts per task, which includes receive iterations that did not actually pick up a message until they hit their timeout (see the <i>receive timeout</i> property).

Default is unlimited (<code>-1</code>) in case of a standard <i>TaskExecutor</i>, reusing the original invoker threads until shutdown (at the expense of limited dynamic scheduling).

In case of a <i>SchedulingTaskExecutor</i> indicating a preference for short-lived tasks, the default is <code>10</code> instead. Specify a number of 10 to 100 messages to balance between rather long-lived and rather short-lived tasks here.

Long-lived tasks avoid frequent thread context switches through sticking with the same thread all the way through, while short-lived tasks allow thread pools to control the scheduling. Hence, thread pools will usually prefer short-lived tasks.

#### Idle consumer limit
Specify the limit for the number of consumers that are allowed to be idle at any given time.

This limit is used to determine if a new invoker should be created. Increasing the limit causes invokers to be created more aggressively. This can be useful to ramp up the number of invokers faster.

The default is <code>1</code>, only scheduling a new invoker (which is likely to be idle initially) if none of the existing invokers is currently idle.

#### Idle task execution limit
Specify the limit for idle executions of a consumer task, not having received any message within its execution. If this limit is reached, the task will shut down and leave receiving to other executing tasks.

The default is <code>1</code>, closing idle resources early once a task didn't receive a message. This applies to dynamic scheduling only; see the <i>max concurrent consumers</i> setting. The minimum number of consumers (see <i>concurrent consumers</i>) will be kept around until shutdown in any case.

Within each task execution, a number of message reception attempts (according to the <i>max messages per task</i> setting) will each wait for an incoming message (according to the <i>receive timeout</i> setting). If all of those receive attempts in a given task return without a message, the task is considered idle with respect to received messages. Such a task may still be rescheduled; however, once it reached the specified <i>idle task execution limit</i>, it will shut down (in case of dynamic scaling).

Raise this limit if you encounter too frequent scaling up and down. With this limit being higher, an idle consumer will be kept around longer, avoiding the restart of a consumer once a new load of messages comes in. Alternatively, specify a higher <i>max messages per task</i> and/or <i>receive timeout</i> value, which will also lead to idle consumers being kept around for a longer time (while also increasing the average execution time of each scheduled task).

#### Acknowledge
JMS acknowledge modes:
- <b>Auto</b>: automatic message acknowledgement <i>before</i> listener execution; no redelivery in case of exception thrown.
- <b>Client</b>: automatic message acknowledgement <i>after</i> successful listener execution; no redelivery in case of exception thrown.
- <b>Dups-ok</b>: <i>lazy</i> message acknowledgement during or after listener execution; <i>potential redelivery</i> in case of exception thrown.
- <b>Transacted</b>: transactional acknowledgement after successful listener execution; <i>guaranteed redelivery</i> in case of exception thrown.

Default is <i>transacted</i> (unless a custom message listener container is provided).

#### Recovery interval
Specifies the interval between recovery attempts, in milliseconds. The default is <code>5000</code> ms (five seconds).

#### Error channel
If a (synchronous) downstream exception is thrown and an <i>error channel</i> is specified, the <code>MessagingException</code> will be sent to this channel; any response from which will be returned as a reply by the gateway.

If an <i>error channel</i> is <b>not</b> supplied, any such exception will be propagated to the listener container and any JMS transaction will be rolled back. Any synchronous downstream exceptions in the error flow will also cause any JMS transaction to be rolled back.

#### Receive timeout
Set the timeout to use for receive calls. The default is <code>1000</code> ms (one second).

Note: this value needs to be smaller than the transaction timeout used by the transaction manager. Value <code>-1</code> indicates no timeout at all; however, this is only feasible if not running within a transaction manager.

#### Request timeout
Set the send timeout value for sending messages to the request channel.

Default is <code>1000</code> (1 second).

#### Reply timeout
Set the receive timeout value for receiving messages from the reply channel.

Default is <code>1000</code> (1 second).

#### Explicit QoS enabled for replies
If <i>true</i>, then the values of <i>delivery persistent</i>, <i>priority</i>, and <i>time to live</i> will be used when sending a message. Otherwise, the default values, that may be set administratively, will be used.

Default is <i>false</i>.

#### Reply time to live
Specifies the time-to-live (in milliseconds) of the message when sending. 

Since a default value may be defined administratively, this is only used when <i>explicit QoS enabled</i> is set to <i>true</i>.

Default is <i>unlimited</i> (<code>0</code>): messages will never expire.

#### Reply priority
Set the priority of a message when sending. 

Since a default value may be defined administratively, this is only used when <i>explicit QoS enabled</i> is set to <i>true</i>.

Default is <code>4</code>.

#### Reply delivery persistant
Specifies whether message delivery should be persistent or non-persistent. This will set the delivery mode accordingly, to either <i>PERSISTENT</i> (true) or <i>NON_PERSISTENT</i> (false).

Since a default value may be defined administratively, this is only used when <i>explicit QoS enabled</i> is set to <i>true</i>.

Default it <i>true</i> (delivery mode <i>PERSISTENT</i>).

#### Connection factory
Reference to a JMS ConnectionFactory used for creating connections.

<i>Required</i>

<b>Note</b>: Don't use a <i>caching connection factory</i> in combination with dynamic scaling. Ideally, don't use it with a inbound gateway at all, since it is generally preferable to let the gateway itself handle appropriate caching within its lifecycle. Also, stopping and restarting a gateway will only work with an independent, locally cached connection - not with an externally cached one.

#### Request destination name
A provider-specific destination name, usually either the name of a <i>JMS queue</i> or <i>JMS topic</i>. 

The JMS message providing system is assumed to send request messages to this destination.

#### Request pub-sub domain
Whether the <i>publish-subscribe</i> domain (JMS Topics) should be used for resolving the request destination name or not.

Default is <i>false</i>, indicating that the <i>point-to-point</i> domain (JMS Queues) should be used.

#### Default reply queue name
Name of the JMS queue where replies are send by this gateway when the <i>reply to</i> destination is not specified on the request message.

#### Default reply topic name
Name of the JMS topic where replies are send by this gateway when the <i>reply to</i> destination is not specified on the request message.

#### Extract request payload
Applies to the <i>JMS message</i> that is received as a request and then converted into a <i>Spring Integration message</i>.

Determines whether the received JMS message body will be extracted. If <code>false</code>, the JMS message itself will become the Spring Integration message payload.

Default is <code>true</code>.

#### Extract reply payload
Applies to the <i>Spring Integration message</i> that is being converted into a <i>JMS message</i> to be sent as the reply.

If you want to pass the whole Spring Integration message (as the body of a JMS <code>ObjectMessage</code>) then set this to <code>false</code>. By default, it is <code>true</code> such that the Spring Integration message payload will be converted into a JMS message (e.g. <code>String</code> payload becomes a JMS <code>TextMessage</code>).

Default is <code>true</code>.

#### Message converter
Reference to a converter for converting the <i>Spring Integration message</i> payload to/from a <i>JMS message</i>. 

When not specified, a <i>SimpleMessageConverter</i> will be used. This converter converts a <i>string</i> to a <i>TextMessage</i>, a <i>byte array</i> to a <code>BytesMessage</code>, a <i>Map</i> to a <code>MapMessage</code>, and a <i>serializable object</i>to an <code>ObjectMessage</code>.

Use a <i>JMS XML Message Converter</i> for XML messages that are not already in a string-representation.

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

