Message bridge
A Message bridge is a relatively trivial endpoint that simply connects two channels or channel adapters. For example, you may want to connect a channel of type queue to a reqular channel so that the endpoint does not have to worry about any polling configuration. Instead, the messaging bridge provides the polling configuration.

By providing an intermediary poller between two channels, a Message bridge can be used to throttle inbound Messages. The poller’s trigger will determine the rate at which messages arrive on the second channel, and the poller’s "maxMessagesPerPoll" property will enforce a limit on the throughput.

Another valid use for a Message bridge is to connect two different systems. In such a scenario, Spring Integration’s role would be limited to making the connection between these systems and managing a poller if necessary. It is probably more common to have at least a Transformer between the two systems to translate between their formats, and in that case, the channels would be provided as the input channel and output channel of a Transformer endpoint. If data format translation is not required, the Messaging Bridge may indeed be sufficient.

Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

Input channel
Channel to consume the input messages from.

<i>Required</i>

Id
Name that uniquely identifies this flow component.

<i>Required</i>


<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-endpoints-chapter.html#endpoint-namespace" target="_blank">Documentation</a>

Specifies when and how the reading task is executed.

Default global poller is used when empty

Use default poller
Specifies if the global (default) poller should be used or an included poller.

The poller specifies when and how the reading task is executed.

If the global poller is used it should be added as separate support object.

Trigger type
A <i>trigger</i> specifies the schedule of the <i>poller</i>.

Trigger types:

<b>1. Fixed delay trigger </b>
Triggers with a <i>periodic constant interval</i>. Each execution is scheduled relative to the <i>actual</i> execution time of the previous execution. If an execution is delayed for any reason (such as garbage collection or other background activity), subsequent executions will be delayed as well. 

<b>2. Fixed rate trigger</b>
Triggers with a <i>periodic constant interval</i>. Each execution is scheduled relative to the <i>scheduled</i> execution time of the initial execution.If an execution is delayed for any reason , two or more executions will occur in rapid succession to "catch up."

<b>3. Cron trigger</b>
Enables the scheduling of tasks based on <i>cron expressions</i>.  Consider using a cron trigger for hourly, daily, and monthly settings. 

Time unit
Specifies the time unit of the <i>fixed delay</i> or <i>fixed rate</i> value.

For hourly, daily or monthly settings, consider using a <i>cron trigger</i> instead.

Default is <code>Milliseconds</code>.

Fixed delay
Time between each two subsequent executions, measured from completion time.

Fixed rate
Time between each two subsequent executions, measured from start time.

Cron
Pattern used by a cron-trigger to specify the trigger schedule.

The pattern is a list of six single space-separated fields, representing <code>second minute hour day month weekday</code>. Month and weekday names can be given as the first three letters of the English names.

Example patterns:

<code>0 0 * * * *</code> = the top of every hour of every day
<code>0 0 8-10 * * *</code> = 8, 9 and 10 o'clock of every day
<code>0 0/30 8-10 * * *</code> = 8:00, 8:30, 9:00, 9:30 and 10 o'clock every day
<code>0 0 9-17 * * MON-FRI</code> = on the hour nine-to-five weekdays
<code>0 0 0 25 12 ?</code> = every Christmas Day at midnight

Max messages per poll
Specifies the <i>maximum number of messages</i> to receive within a given poll operation. 

The poller will continue trying to receive without waiting until either no message is available or this maximum is reached.

For example, if a poller has a 10 second interval trigger and a <i>maxMessagesPerPoll</i> setting of 25, and it is polling a channel that has 100 messages in its queue, all 100 messages can be retrieved within 40 seconds. It grabs 25, waits 10 seconds, grabs the next 25, and so on. 

Default is 1.

Receive timeout
Specifies the <i>amount of time</i> the poller should wait if no messages are available when receiving.

Send timeout
Specifies the timeout for sending out messages.

Task executor
Task executor to execute the scheduled tasks. 

Default when empty: TaskScheduler with name 'taskScheduler', created if not exists.

Task executor
The channel that error messages will be sent to if a failure occurs in this poller's invocation. To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.

