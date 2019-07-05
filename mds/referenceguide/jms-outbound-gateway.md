---
id: jms-outbound-gateway
title: JMS outbound gateway
sidebar_label: JMS outbound gateway
---
#### Sends JMS request messages to a connection and receives JMS reply messages.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/jms.html#jms-outbound-gateway" target="_blank">Documentation</a>

Sends JMS request messages to the specified request destination at the connection created by the <i>connection factory</i>, and receives JMS reply messages from the specified reply destination using the same <i>connection factory</i>.

#### Connection factory
Reference to a JMS connection factory used for creating connections.

<i>Required</i>

<b>Note</b>: The connection factory should return pooled connections as well as pooled sessions and message producers, otherwise performance of JMS operations is going to suffer. Consider using a <i>caching connection factory</i> to achieve this.

#### Request destination name
Name of the destination to which JMS request messages will be sent (typically the name of a JMS queue or topic).

This attribute is mutually exclusive with <i>request destination expression</i>.

#### Request pub-sub domain
Whether the <i>publish-subscribe</i> domain (JMS Topics) should be used for resolving the request destination name or not.

Default is <i>false</i>, indicating that the <i>point-to-point</i> domain (JMS Queues) should be used.

#### Reply destination name
Name of the destination from which JMS reply messages will be received (typically the name of a JMS queue or topic).

If not provided, JMS temporary queues will be created.

#### Reply pub-sub domain
Whether the <i>publish-subscribe</i> domain (JMS Topics) should be used for resolving the reply destination name or not.

Default is <i>false</i>, indicating that the <i>point-to-point</i> domain (JMS Queues) should be used.

#### Extract request payload
Applies to the <i>Spring Integration message</i> that is being converted into a <i>JMS message</i> to be sent as a request.

If you want to pass the whole Spring Integration message (as the body of a JMS <code>ObjectMessage</code>) then set this to <code>false</code>. By default, it is <code>true</code> such that the Spring Integration message payload will be converted into a JMS message (e.g. <code>String</code> payload becomes a JMS <code>TextMessage</code>). In both cases, the message headers will be mapped to JMS headers/properties.

Default is <code>true</code>.

#### Extract reply payload
Applies to the <i>JMS message</i> that is received as a reply and then converted into a <i>Spring Integration message</i>.

Determines whether the received JMS message body will be extracted. If <code>false</code>, the JMS message itself will become the Spring Integration message payload. In both cases, the JMS Message headers/properties will be mapped to message headers.

The default is <code>true</code>.

#### Message converter
Reference to a converter for converting the <i>Spring Integration message</i> payload to/from a <i>JMS message</i>. 

When not specified, a <i>SimpleMessageConverter</i> will be used. This converter converts a <i>string</i> to a <i>TextMessage</i>, a <i>byte array</i> to a <code>BytesMessage</code>, a <i>Map</i> to a <code>MapMessage</code>, and a <i>serializable object</i>to an <code>ObjectMessage</code>.

Use a <i>JMS XML Message Converter</i> for XML messages that are not already in a string-representation.

#### Request destination expression
A SpEL expression to be evaluated at runtime against each Spring Integration request message as the root object. The result should be the request destination name.

This attribute is mutually exclusive with <i>request destination name</i>.

#### Reply destination expression
A SpEL expression to be evaluated at runtime against each Spring Integration request message as the root object. The result should be the reply destination name.

This attribute is mutually exclusive with <i>reply destination name</i>.

#### Correlation key
Provide the name of a JMS property that should hold a generated UUID that the receiver of the JMS message would expect to represent the <i>CorrelationID</i>.

When waiting for the reply message, a message selector will be configured to match this property name and the UUID value that was sent in the request.

If <b>no</b> value is provided for this attribute, then the reply consumer's message selector will be expecting the <i>JMSCorrelationID</i> to equal the message ID of the request. If you want to store the outbound correlation UUID value in the actual <i>JMSCorrelationID</i> property, then set this value to <code>"JMSCorrelationID"</code>; any other value will be treated as a JMS string property.

Note: when using a <i>reply listener</i> the correlation data includes a UUID representing the gateway as well as a message identifier. For this reason, the use of a <i>reply listener</i> requires the specification of a correlation key if an explicit reply destination is provided.

#### Receive timeout
Timeout for the JMS message consumer to receive the JMS reply message.

Default is <code>5000</code> (five seconds).

#### Reply timeout
Allows you to specify how long (in milliseconds) this gateway will wait for the reply message to be sent successfully to the reply channel before throwing an exception. This attribute only applies when the channel might block, for example when using a bounded queue channel that is currently full.

Also, keep in mind that when sending to a <i>direct channel</i>, the invocation will occur in the sender's thread. Therefore, the failing of the send operation may be caused by other components further downstream.

If not specified, by default the gateway will wait indefinitely.

#### Explicit QoS enabled
If <i>true</i>, then the values of <i>delivery persistent</i>, <i>priority</i>, and <i>time to live</i> will be used when sending a message. Otherwise, the default values, that may be set administratively, will be used.

Default is <i>false</i>.

#### Delivery persistent
Specifies whether message delivery should be persistent or non-persistent. This will set the delivery mode accordingly, to either <i>PERSISTENT</i> (true) or <i>NON_PERSISTENT</i> (false).

Since a default value may be defined administratively, this is only used when <i>explicit QoS enabled</i> is set to <i>true</i>.

Default it <i>true</i> (delivery mode <i>PERSISTENT</i>).

#### Priority
Set the priority of a message when sending. 

Since a default value may be defined administratively, this is only used when <i>explicit QoS enabled</i> is set to <i>true</i>.

Default is <code>4</code>.

#### Time to live
Specifies the time-to-live (in milliseconds) of the message when sending. 

Since a default value may be defined administratively, this is only used when <i>explicit QoS enabled</i> is set to <i>true</i>.

Default is <i>unlimited</i> (<code>0</code>): messages will never expire.

#### Task executor
A reference to a task executor for receiving the replies and handing them over to the sending thread.

Default is a <code>SimpleAsyncTaskExecutor</code>.

#### Requires reply
Specify whether this outbound gateway must return a non-<code>null</code> value, i.e. whether every request message must result in a reply message.

If <code>true</code>, a <code>ReplyRequiredException</code> will be thrown when the underlying service returns a <code>null</code> value.

Default is <code>true</code>.

#### Use reply listener
If enabled, instead of creating a consumer for each reply, a <code>MessageListener</code> container is used to receive the replies and hand them over to the requesting thread. This provides a number of performance benefits as well as alleviating the cached consumer memory utilization problem (see the <i>cache consumers</i> property of the <i>JMS caching connection factory</i>).

When using a <i>reply listener</i>, instead of creating a <code>TemporaryQueue</code> for each request, a single <code>TemporaryQueue</code> is used (the gateway will create an additional <code>TemporaryQueue</code>, as necessary, if the connection to the broker is lost and recovered).

When using a <i>correlation key</i>, multiple gateways can share the same <i>reply destination</i> because the listener container uses a selector that is unique to each gateway.

<b><i>Caution</i></b>
If you specify a <i>reply listener</i> and a <i>reply destination name</i>, but provide <b>no</b> <i>correlation key</i>, the gateway will log a warning and not use a reply listener. This is because there is no way to configure a selector in this case, thus there is no way to avoid a reply going to a different gateway that might be configured with the same reply destination.

 Note that, in this situation, a new consumer is used for each request, and consumers can build up in memory as described above; therefore cached consumers should not be used in this case.

#### Idle reply listener timeout
When using a reply listener, specify whether the container should be started on-demand and stopped when idle for this time (in seconds). When omitted (or zero or less), the reply container is started/stopped according to the gateway's lifecycle.

Default is empty.

#### Async
When <code>false</code> (default), the requesting thread is suspended until a reply is received or a timeout occurs.

When <code>true</code>, the requesting thread is released and the reply is returned on the listener container thread.

#### Acknowledge
JMS acknowledge modes:
- <b>Auto</b> (default): automatic message acknowledgment <i>before</i> listener execution; no redelivery in case of exception thrown.
- <b>Client</b>: automatic message acknowledgment <i>after</i> successful listener execution; no redelivery in case of exception thrown.
- <b>Dups-ok</b>: <i>lazy</i> message acknowledgment during or after listener execution; <i>potential redelivery</i> in case of exception thrown.
- <b>Transacted</b>: transactional acknowledgment after successful listener execution; <i>guaranteed redelivery</i> in case of exception thrown.

#### Concurrent consumers
Specify the number of concurrent consumers to create.

Default is <code>1</code>.

Specifying a higher value for this setting will increase the standard level of scheduled concurrent consumers at runtime: This is effectively the minimum number of concurrent consumers which will be scheduled at any given time. This is a static setting; for dynamic scaling, consider specifying the <i>max concurrent consumers</i> setting instead.

<b>Do not raise the number of concurrent consumers for a topic, unless vendor-specific setup measures clearly allow for it.</b> With regular setup, this would lead to concurrent consumption of the same message, which is hardly ever desirable.

#### Max. concurrent consumers
Specify the maximum number of concurrent consumers to create.

Default is <code>1</code>.

If this setting is higher than <i>concurrent consumers</i>, the listener container will dynamically schedule new consumers at runtime, provided that enough incoming messages are encountered. Once the load goes down again, the number of consumers will be reduced to the standard level again.

Raising the number of concurrent consumers is recommendable in order to scale the consumption of messages coming in from a queue. However, note that any ordering guarantees are lost once multiple consumers are registered. In general, stick with 1 consumer for low-volume queues.

<b>Do not raise the number of concurrent consumers for a topic, unless vendor-specific setup measures clearly allow for it.</b> With regular setup, this would lead to concurrent consumption of the same message, which is hardly ever desirable.

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

#### Recovery interval
Specifies the interval between recovery attempts, in milliseconds. The default is <code>5000</code> ms (five seconds).

#### Idle consumer limit
Specify the limit for the number of consumers that are allowed to be idle at any given time.

This limit is used to determine if a new invoker should be created. Increasing the limit causes invokers to be created more aggressively. This can be useful to ramp up the number of invokers faster.

The default is <code>1</code>, only scheduling a new invoker (which is likely to be idle initially) if none of the existing invokers is currently idle.

#### Idle task execution limit
Specify the limit for idle executions of a consumer task, not having received any message within its execution. If this limit is reached, the task will shut down and leave receiving to other executing tasks.

The default is <code>1</code>, closing idle resources early once a task didn't receive a message. This applies to dynamic scheduling only; see the <i>max concurrent consumers</i> setting. The minimum number of consumers (see <i>concurrent consumers</i>) will be kept around until shutdown in any case.

Within each task execution, a number of message reception attempts (according to the <i>max messages per task</i> setting) will each wait for an incoming message (according to the <i>receive timeout</i> setting). If all of those receive attempts in a given task return without a message, the task is considered idle with respect to received messages. Such a task may still be rescheduled; however, once it reached the specified <i>idle task execution limit</i>, it will shut down (in case of dynamic scaling).

Raise this limit if you encounter too frequent scaling up and down. With this limit being higher, an idle consumer will be kept around longer, avoiding the restart of a consumer once a new load of messages comes in. Alternatively, specify a higher <i>max messages per task</i> and/or <i>receive timeout</i> value, which will also lead to idle consumers being kept around for a longer time (while also increasing the average execution time of each scheduled task).

#### Receive timeout
Set the timeout to use for receive calls. The default is <code>1000</code> ms (one second).

Note: this value needs to be smaller than the transaction timeout used by the transaction manager. Value <code>-1</code> indicates no timeout at all; however, this is only feasible if not running within a transaction manager.

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

