# JMS message driven channel adapter
#### Polls a specific destination on a JMS server for messages.
<a href="http://docs.spring.io/spring-integration/docs/2.2.x/reference/html/jms.html#jms-inbound-channel-adapter" target="_blank">Documentation</a>

Receives JMS messages from the specified destination at the connection created by the <i>connection factory</i>.

Note that this inbound channel adapter is a polling consumer. <b>This should only be used in situations where polling is done relatively infrequently and timeliness is not important.</b> For all other situations (a vast majority of JMS-based use-cases), the <i>JMS message driven channel adapter</i> is a better option.

Also note that in contrast to the <i>JMS message driven channel adapter</i>, this channel adapter does not register a consumer on the JMS destination that is always present. This means that you cannot detect any "missing consumers" on JMS queues/topics when using these polling consumers (although when using a <i>caching connection factory</i> that caches consumers combined with a low polling interval, the behaviour will appear to be the same).

#### Selector
A JMS message selector boolean expression that evaluates the headers of the messages. Only the messages where this expression evaluates to <code>true</code> are received.

See the java JMS specification for message selector syntax:
<a href="http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html" target="_blank">http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html</a>

#### Extract payload
If enabled, the received JMS Message will be converted by the <i>message converter</i>. The converted message is set as payload of the result Spring message. If disabled,  the result message will contain the raw JMS message as payload.

Default is <code>true</code>.

#### Acknowledge
JMS acknowledge modes:
- <b>Auto</b> (default): automatic message acknowledgment <i>before</i> listener execution; no redelivery in case of exception thrown.
- <b>Client</b>: automatic message acknowledgment <i>after</i> successful listener execution; no redelivery in case of exception thrown.
- <b>Dups-ok</b>: <i>lazy</i> message acknowledgment during or after listener execution; <i>potential redelivery</i> in case of exception thrown.
- <s><b>Transacted</b>: transactional acknowledgment after successful listener execution; <i>guaranteed redelivery</i> in case of exception thrown.</s>

The last option, <i>transacted</i>, does not work because of the polling behaviour of this adapter. If transactional message processing is important, enable the <i>session transacted</i> option or consider using a <i>JMS message driven channel adapter</i> instead.

#### Session transacted
Setting this option to <code>true</code> enables transactions.

Default is <code>false</code>.

#### Receive timeout
Set the timeout to use for receive calls. The default is <code>1000</code> ms (one second).

Note: this value needs to be smaller than the transaction timeout used by the transaction manager. Value <code>-1</code> indicates no timeout at all; however, this is only feasible if not running within a transaction manager.

#### Connection factory
Reference to a <i>JMS connection factory</i> used for creating connections.

<i>Required</i>

<b>Note</b>: When polling for messages frequently, the connection factory should return pooled connections as well as pooled sessions, otherwise performance of JMS operations is going to suffer. Consider using a <i>caching connection factory</i> to achieve this.

#### Destination name
A provider-specific destination name, usually either the name of a <i>JMS queue</i> or <i>JMS topic</i>. 

The JMS message providing system is assumed to send messages to this destination.

#### Pub-sub domain
Whether the <i>publish-subscribe</i> domain (JMS Topics) should be used for resolving the destination name or not.

Default is <i>false</i>, indicating that the <i>point-to-point</i> domain (JMS Queues) should be used.

#### Message converter
Reference to a converter for converting the <i>Spring Integration message</i> payload to/from a <i>JMS message</i>. 

When not specified, a <i>SimpleMessageConverter</i> will be used. This converter converts a <i>string</i> to a <i>TextMessage</i>, a <i>byte array</i> to a <code>BytesMessage</code>, a <i>Map</i> to a <code>MapMessage</code>, and a <i>serializable object</i>to an <code>ObjectMessage</code>.

Use a <i>JMS XML Message Converter</i> for XML messages that are not already in a string-representation.


<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-endpoints-chapter.html#endpoint-namespace" target="_blank">Documentation</a>

Specifies when and how the reading task is executed.

Default global poller is used when empty

#### Use default poller
Specifies if the global (default) poller should be used or an included poller.

The poller specifies when and how the reading task is executed.

If the global poller is used it should be added as separate support object.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

#### Trigger type
A <i>trigger</i> specifies the schedule of the <i>poller</i>.

Trigger types:

<b>1. Fixed delay trigger </b>
Triggers with a <i>periodic constant interval</i>. Each execution is scheduled relative to the <i>actual</i> execution time of the previous execution. If an execution is delayed for any reason (such as garbage collection or other background activity), subsequent executions will be delayed as well. 

<b>2. Fixed rate trigger</b>
Triggers with a <i>periodic constant interval</i>. Each execution is scheduled relative to the <i>scheduled</i> execution time of the initial execution.If an execution is delayed for any reason , two or more executions will occur in rapid succession to "catch up."

<b>3. Cron trigger</b>
Enables the scheduling of tasks based on <i>cron expressions</i>.  Consider using a cron trigger for hourly, daily, and monthly settings. 


#### Time unit
Specifies the time unit of the <i>fixed delay</i> or <i>fixed rate</i> value.

For hourly, daily or monthly settings, consider using a <i>cron trigger</i> instead.

Default is <code>Milliseconds</code>.

#### Fixed delay
Time between each two subsequent executions, measured from completion time.

#### Fixed rate
Time between each two subsequent executions, measured from start time.

#### Cron
Pattern used by a cron-trigger to specify the trigger schedule.

The pattern is a list of six single space-separated fields, representing <code>second minute hour day month weekday</code>. Month and weekday names can be given as the first three letters of the English names.

Example patterns:

<code>0 0 * * * *</code> = the top of every hour of every day
<code>0 0 8-10 * * *</code> = 8, 9 and 10 o'clock of every day
<code>0 0/30 8-10 * * *</code> = 8:00, 8:30, 9:00, 9:30 and 10 o'clock every day
<code>0 0 9-17 * * MON-FRI</code> = on the hour nine-to-five weekdays
<code>0 0 0 25 12 ?</code> = every Christmas Day at midnight

#### Max messages per poll
Specifies the <i>maximum number of messages</i> to receive within a given poll operation. 

The poller will continue trying to receive without waiting until either no message is available or this maximum is reached.

For example, if a poller has a 10 second interval trigger and a <i>maxMessagesPerPoll</i> setting of 25, and it is polling a channel that has 100 messages in its queue, all 100 messages can be retrieved within 40 seconds. It grabs 25, waits 10 seconds, grabs the next 25, and so on. 

Default is 1.


#### Receive timeout
Specifies the <i>amount of time</i> the poller should wait if no messages are available when receiving.

#### Send timeout
Specifies the timeout for sending out messages.

#### Task executor
Task executor to execute the scheduled tasks. 

Default when empty: TaskScheduler with name 'taskScheduler', created if not exists.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this poller's invocation. To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.

#### Actively receives messages from a specific destination on a JMS server.
<a href="http://docs.spring.io/spring-integration/docs/2.2.x/reference/html/jms.html#jms-message-driven-channel-adapter" target="_blank">Documentation</a>

Receives JMS messages from the specified destination at the connection created by the <i>connection factory</i>.

The JMS server will actively push messages to this channel adapter when they become available, resulting in message driven, real-time communication. In the vast majority of JMS-based use-cases, this approach is preferable to the polling approach of the <i>JMS inbound channel adapter</i>.

#### Selector
A JMS message selector boolean expression that evaluates the headers of the messages. Only the messages where this expression evaluates to <code>true</code> are received.

See the java JMS specification for message selector syntax:
<a href="http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html" target="_blank">http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html</a>

#### Extract payload
If enabled, the received JMS Message will be converted by the <i>message converter</i>. The converted message is set as payload of the result Spring message. If disabled,  the result message will contain the raw JMS message as payload.

Default is <code>true</code>.

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

#### Max concurrent consumers
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

#### Max messages per task
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

#### Error channel
If a (synchronous) downstream exception is thrown and an <i>error-channel</i> is specified, the <i>MessagingException</i> will be sent to this channel. Otherwise, any such exception will be propagated to the listener container and any JMS transaction will be rolled back. Any synchronous downstream exceptions in the error flow will also cause any JMS transaction to be rolled back.

#### Recovery interval
Specifies the interval between recovery attempts, in milliseconds.

The default is <code>5000</code> ms (five seconds).

#### Receive timeout
Set the timeout to use for receive calls. The default is <code>1000</code> ms (one second).

Note: this value needs to be smaller than the transaction timeout used by the transaction manager. Value <code>-1</code> indicates no timeout at all; however, this is only feasible if not running within a transaction manager.

#### Send timeout
The timeout value for sending messages.

If not explicitly configured, the default is <code>1000</code> ms (one second).

#### Connection factory
Reference to a <i>JMS connection factory</i> used for creating connections.

<i>Required</i>

<b>Note</b>: Don't use a <i>caching connection factory</i> in combination with dynamic scaling. Ideally, don't use it with a message driven channel adapter at all, since it is generally preferable to let the adapter itself handle appropriate caching within its lifecycle. Also, stopping and restarting an adapter will only work with an independent, locally cached connection - not with an externally cached one.

#### Destination name
A provider-specific destination name, usually either the name of a <i>JMS queue</i> or <i>JMS topic</i>. 

The JMS message providing system is assumed to send messages to this destination.

#### Pub-sub domain
Whether the <i>publish-subscribe</i> domain (JMS Topics) should be used for resolving the destination name or not.

Default is <i>false</i>, indicating that the <i>point-to-point</i> domain (JMS Queues) should be used.

#### Message converter
Reference to a converter for converting the <i>Spring Integration message</i> payload to/from a <i>JMS message</i>. 

When not specified, a <i>SimpleMessageConverter</i> will be used. This converter converts a <i>string</i> to a <i>TextMessage</i>, a <i>byte array</i> to a <code>BytesMessage</code>, a <i>Map</i> to a <code>MapMessage</code>, and a <i>serializable object</i>to an <code>ObjectMessage</code>.

Use a <i>JMS XML Message Converter</i> for XML messages that are not already in a string-representation.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

