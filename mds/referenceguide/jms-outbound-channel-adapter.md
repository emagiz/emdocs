# JMS outbound channel adapter
#### Sends messages to a JMS destination.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/jms.html#jms-outbound-channel-adapter" target="_blank">Documentation</a>

Sends JMS messages to the specified destination at the connection created by the <i>Connection factory</i>

The other system is assumed to receive the JMS Messages from the <i>JMS Destination</i>. <br/>This system may or may not be a Spring Integration application. Of course, when sending the Spring Integration Message instance as the body of the JMS Message itself (with the 'extract-payload' value set to false), it is assumed that the other system is based on Spring Integration. 

If necessary, the message payload can be extracted and transformed using a converter.

#### Destination expression
A SpEL expression to be evaluated at runtime against each message. The result should be a string representing the destination name. If the evaluation result is <code>null</code>, messages will be sent to the default destination of the underlying <code>JmsTemplate</code>.

This attribute is mutually exclusive with <i>destination name</i>.

#### Session transacted
Setting this option to <code>true</code> enables transactions for the message send. If there is already a JMS transaction in process, perhaps from a <i>JMS message driven channel adapter</i> upstream, the same transaction is used; otherwise a new transaction is started.

Default is <code>false</code>.

#### Explicit QoS enabled
If <i>true</i>, then the values of <i>deliveryPersistent</i>, <i>priority</i>, and <i>timeToLive</i> will be used when sending a message. Otherwise, the default values, that may be set administratively, will be used.

Default is <i>false</i>.

#### Delivery persistent
Specifies whether message delivery should be persistent or non-persistent. This will set the delivery mode accordingly, to either <i>PERSISTENT</i> (true) or <i>NON_PERSISTENT</i> (false).

Since a default value may be defined administratively, this is only used when <i>explicitQosEnabled</i> is set to <i>true</i>.

Default it <i>true</i> (delivery mode <i>PERSISTENT</i>).

#### Priority
Set the priority of a message when sending. 

Since a default value may be defined administratively, this is only used when <i>explicitQosEnabled</i> is set to <i>true</i>.

Default is <code>4</code>.

#### Time to live
Specifies the time-to-live (in milliseconds) of the message when sending. 

Since a default value may be defined administratively, this is only used when <i>explicitQosEnabled</i> is set to <i>true</i>.

Default is <i>unlimited</i> (<code>0</code>): messages will never expire.

#### Connection factory
Reference to a <i>JMS connection factory</i> used for creating connections.

<i>Required</i>

<b>Note</b>: The connection factory should return pooled connections as well as pooled sessions and message producers, otherwise performance of JMS operations is going to suffer. Consider using a <i>caching connection factory</i> to achieve this.

#### Destination name
Name of the destination to which JMS Messages will be sent (typically the name of a JMS queue or topic).

This attribute is mutually exclusive with <i>destination expression</i>.

#### Pub-sub domain
Whether the <i>publish-subscribe</i> domain (JMS Topics) should be used for resolving the destination name or not.

Default is <i>false</i>, indicating that the <i>point-to-point</i> domain (JMS Queues) should be used.

#### Extract payload
If enabled, the Spring message payload will be converted by the <i>Message converter</i> and passed as the JMS Message body. If disabled,  the Spring Integration Message itself is passed as the JMS Message body.

Default: true

#### Message converter
Reference to a converter for converting the <i>Spring Integration message</i> payload to/from a <i>JMS message</i>. 

When not specified, a <i>SimpleMessageConverter</i> will be used. This converter converts a <i>string</i> to a <i>TextMessage</i>, a <i>byte array</i> to a <code>BytesMessage</code>, a <i>Map</i> to a <code>MapMessage</code>, and a <i>serializable object</i>to an <code>ObjectMessage</code>.

Use a <i>JMS XML Message Converter</i> for XML messages that are not already in a string-representation.


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel to consume messages from.

<i>Required</i>


<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-endpoints-chapter.html#endpoint-namespace" target="_blank">Documentation</a>

Specifies when and how the reading task is executed.

Default global poller is used when empty

#### Use default poller
Specifies if the global (default) poller should be used or an included poller.

The poller specifies when and how the reading task is executed.

If the global poller is used it should be added as separate support object.

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

