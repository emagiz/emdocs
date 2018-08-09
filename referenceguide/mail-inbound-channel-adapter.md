# Mail inbound channel adapter
#### Defines an inbound Channel Adapter that polls a mailbox for mail messages.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/mail.html#mail-inbound" target="_blank">Documentation</a>

Hint: If you do have IMAP idle support, use "imap-idle-channel-adapter" element instead. 

Since the "idle" command enables event-driven notifications, no poller is necessary for this adapter. It will send a Message to the specified channel as soon as it receives the notification that new mail is available.

#### Should delete messages
Specify whether mail messages should be deleted after retrieval.

#### Should mark messages as read
Specify whether mail messages should be marked as read after being retrieved (not supported by all mail servers, e.g. POP3).

#### User flag
Specify the user flag to mark messages read by the adapter when the mail store does not support the RECENT flag but does support user flags (keywords). This flag is set regardless of the <i>should mark messages as read</i> attribute. It is used by the default search strategy to ignore already processed messages.

Default is <code>spring-integration-mail-adapter</code>.

#### Mail filter expression
Allows you to provide a SpEL expression which defines a fine grained filtering criteria for the mail messages to be processed by this adapter.

#### Max fetch size
Specify the maximum number of mail messages to fetch per receive call.	

#### Mail properties
Reference to a <i>Properties</i> entity that contains mail properties.


<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-endpoints-chapter.html#endpoint-namespace" target="_blank">Documentation</a>

Specifies when and how the reading task is executed.

Default global poller is used when empty

#### Use default poller
Specifies if the global (default) poller should be used or an included poller.

The poller specifies when and how the reading task is executed.

If the global poller is used it should be added as separate support object.

#### Store URI
The URI for the mail store. 

Typically looks like the following (the underlined words need to be replaced by the actual values):
<code>(pop3[s]|imap[s])://<u>user</u>:<u>password</u>@<u>host</u>[:<u>port</u>]/INBOX</code>

Note that you can use property placeholders within the URI, for example:
<code>imaps://${username}:${password}@imap.gmail.com/INBOX</code>

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

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

