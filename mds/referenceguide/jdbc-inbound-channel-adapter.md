---
id: jdbc-inbound-channel-adapter
title: JDBC inbound channel adapter
sidebar_label: JDBC inbound channel adapter
---
#### Generates messages by polling a database using an SQL query.
<a href="http://docs.spring.io/spring-integration/docs/2.2.x/reference/html/jdbc.html#jdbc-inbound-channel-adapter" target="_blank">Documentation</a>

Inbound channel adapter that generates messages by executing an SQL SELECT query on a database, creating messages from the query result.

Optionally this adapter can also execute an SQL UPDATE statement to mark the records returned by the SELECT query as processed, so that they don't show up in the next poll.

#### SQL data source
Reference to a JDBC data source, usually including some form of connection pooling, used for accessing the database.

<i>Required</i>

#### SQL query
A SELECT query to execute when a message is polled. The result of this query will be the body of the outgoing message.

The query can return multiple rows; if you want to convert rows in the SELECT query result to individual messages you can use a downstream splitter.

<i>Required</i>

#### SQL update
An optional UPDATE statement that is being used to mark the records returned by the SELECT query as processed, so that they don't show up in the next poll.

Note that you can use the values of columns from the SELECT query result as parameters in the UPDATE query by prefixing the name with a colon.

An example of an UPDATE query that uses the 'id' values from the SELECT query:
<code>SELECT * from mytable WHERE processed = FALSE</code>
<code>UPDATE mytable SET processed = TRUE where id IN (:id)</code>

<i>Optional</i>

#### Maximum rows per poll
Limits the number of rows extracted per query.

If not specified all rows are extracted into the outgoing message.

<i>Optional</i>

#### Update per row
Flag to indicate whether the update query should be executed per message, or per row (in the case that a message contains multiple rows).

Default is <code>false</code>, i.e. the update query is executed once per message.

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

