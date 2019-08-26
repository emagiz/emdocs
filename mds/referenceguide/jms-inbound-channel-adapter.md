---
id: jms-inbound-channel-adapter
title: JMS inbound channel adapter
sidebar_label: JMS inbound channel adapter
---
#### Polls a specific destination on a JMS server for messages.
<a href="http://docs.spring.io/spring-integration/docs/2.2.x/reference/html/jms.html#jms-inbound-channel-adapter" target="_blank">Documentation</a>

Receives JMS messages from the specified destination at the connection created by the <i>connection factory</i>.

Note that this inbound channel adapter is a polling consumer. <b>This should only be used in situations where polling is done relatively infrequently and timeliness is not important.</b> For all other situations (a vast majority of JMS-based use-cases), the <i>JMS message driven channel adapter</i> is a better option.

Also note that in contrast to the <i>JMS message driven channel adapter</i>, this channel adapter does not register a consumer on the JMS destination that is always present. This means that you cannot detect any "missing consumers" on JMS queues/topics when using these polling consumers (although when using a <i>caching connection factory</i> that caches consumers combined with a low polling interval, the behaviour will appear to be the same).

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

#### Selector
A JMS message selector boolean expression that evaluates the headers of the messages. Only the messages where this expression evaluates to <code>true</code> are received.

See the java JMS specification for message selector syntax:
<a href="http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html" target="_blank">http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html</a>

#### Extract payload
If enabled, the received JMS Message will be converted by the <i>message converter</i>. The converted message is set as payload of the result Spring message. If disabled,  the result message will contain the raw JMS message as payload.

Default is <code>true</code>.

#### Header mapper
Maps messages headers to and from JMS headers and properties.

By default a <code>DefaultJmsHeaderMapper</code> is used, which will map JMS API headers to/from the corresponding headers of the JMS message and other headers to/from the general properties of the JMS message.

Headers with data types not supported by JMS and headers with names that are not valid Java identifiers will be silently skipped. Headers with names longer than 256 characters or string values longer than 1024 character will be silently skipped as well. Note that skipping these does not mean the headers are "lost": if the full Spring message is serialized and send as the payload of the JMS message, all headers will be preserved that way.

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

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>


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

