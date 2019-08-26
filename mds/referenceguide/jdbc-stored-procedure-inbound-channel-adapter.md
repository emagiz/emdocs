---
id: jdbc-stored-procedure-inbound-channel-adapter
title: JDBC stored procedure inbound channel adapter
sidebar_label: JDBC stored procedure inbound channel adapter
---
#### Generates messages by polling a database using a stored procedure.
<a href="http://static.springsource.org/spring-integration/docs/2.1.x/reference/html/jdbc.html#stored-procedure-inbound-channel-adapter" target="_blank">External documentation</a>

The inbound JDBC stored procedure adapter polls a database using a stored procedure or function call. 

Results of the adapter can be transformed to xml using the <i>JDBC result transformer</i>.

#### Stored procedure name
Specifies the name of the stored procedure. If the stored procedure is a function, this attribute specifies the function name. 

#### Is a function
If <code>true</code>, a SQL function is called. In that case the <i>stored procedure name</i> attribute defines the name of the called function. 

Defaults to <code>false</code>.

e.g. Functions in PostgreSQL require this attribute to be set to <code>true</code>.

#### SQL data source
Reference to a JDBC data source, usually including some form of connection pooling, used for accessing the database.

<i>Required</i>


Specify the stored procedure or function call input parameters here.

#### Stored procedure name expression
The name of the stored procedure provided as a SpEL expression.

Components that use a message as source of parameters have full access to the message and its headers, in order to derive a stored procedure name.

<i>Optional</i> ; mutually exclusive with <i>stored procedure name</i>.

#### Ignore column meta data
Fully supported databases, can automatically retrieve the parameter definition information for the to be invoked Stored Procedure or Function from the JDBC Meta-data.

However, if the used database does not support meta data lookups or if you like to provide customized parameter definitions, this flag can be set to <code>true</code>. 

It defaults to <code>false</code>.
                            
<b>Fully Supported Databases (Stored Procedures):</b>
 * Apache Derby
 * DB2
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL
 * Sybase

<b>Fully Supported Databases (Functions):</b>
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL

#### Skip undeclared results
If this attribute is set to <code>true</code>, then all results from a stored procedure call that don't have a corresponding <i>SQL parameter definition</i> will be bypassed.

E.g. Stored Procedures may return an update count value, even though your Stored Procedure only declared a single result parameter. The exact behavior depends on the used database.

The value is set on the underlying <code>JdbcTemplate</code>.

Only few developers will probably ever like to process update counts, thus the value defaults to <code>true</code>.

#### Expect single result
This attribute indicates that only one result object shall be returned from the stored procedure/function call. If set to <code>true</code> and the result map from the stored procedure/function call contains only 1 element, then that 1 element is extracted and returned as payload.

If the result map contains more than 1 element and expect single result is <code>true</code>, then a <code>MessagingException</code> is thrown.

Otherwise the complete result map is returned as the payload.

Important Note: Several databases such as H2 are not fully supported for stored procedure and/or function calls.

The H2 database, for example, does not fully support the <code>CallableStatement</code> semantics and when executing function calls against H2, a result list is returned, rather than a single value.

#### Return value required
Indicates the procedure's return value should be included in the results returned.

Default is <code>false</code>.

#### JDBC call operations cache size
Defines the maximum number of cached <code>SimpleJdbcCallOperations</code> instances.

Basically, for each stored procedure name a new <code>SimpleJdbcCallOperations</code> instance is created that in return is being cached.

The default cache size is <code>10</code>. A value of <code>0</code> disables caching.


SQL parameter definitions define the type and value of each parameter.

If you are using a database that is fully supported, you typically don't have to specify the stored procedure parameter definitions.

Instead, those parameters can be automatically derived from the JDBC meta-data. However, if you are using databases that are not fully supported or if you like to provide customized parameter definitions, you can set those parameters explicitly. See also the <i>ignore column meta-data</i> attribute.

Note that the <i>order</i>, <i>name</i>, <i>type</i>, <i>direction</i> and <i>scale</i> of the SQL parameters should <b>exactly match</b> the settings specified on the database.

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>


<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/messaging-endpoints-chapter.html#endpoint-namespace" target="_blank">External documentation</a>

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

---
id: jdbc-stored-procedure-inbound-channel-adapter
title: JDBC stored procedure inbound channel adapter
sidebar_label: JDBC stored procedure inbound channel adapter
---
#### Generates messages by polling a database using a stored procedure.
<a href="http://static.springsource.org/spring-integration/docs/2.1.x/reference/html/jdbc.html#stored-procedure-inbound-channel-adapter" target="_blank">Documentation</a>

The inbound JDBC stored procedure adapter polls a database using a stored procedure or function call. 

Results of the adapter can be transformed to xml using the <i>JDBC result transformer</i>.

#### Stored procedure name
Specifies the name of the stored procedure. If the stored procedure is a function, this attribute specifies the function name. 

#### Is a function
If <code>true</code>, a SQL function is called. In that case the <i>stored procedure name</i> attribute defines the name of the called function. 

Defaults to <code>false</code>.

e.g. Functions in PostgreSQL require this attribute to be set to <code>true</code>.

#### SQL data source
Reference to a JDBC data source, usually including some form of connection pooling, used for accessing the database.

<i>Required</i>


Specify the stored procedure or function call input parameters here.

#### Stored procedure name expression
The name of the stored procedure provided as a SpEL expression.

Components that use a message as source of parameters have full access to the message and its headers, in order to derive a stored procedure name.

<i>Optional</i> ; mutually exclusive with <i>stored procedure name</i>.

#### Ignore column meta data
Fully supported databases, can automatically retrieve the parameter definition information for the to be invoked Stored Procedure or Function from the JDBC Meta-data.

However, if the used database does not support meta data lookups or if you like to provide customized parameter definitions, this flag can be set to <code>true</code>. 

It defaults to <code>false</code>.
                            
<b>Fully Supported Databases (Stored Procedures):</b>
 * Apache Derby
 * DB2
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL
 * Sybase

<b>Fully Supported Databases (Functions):</b>
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL

#### Skip undeclared results
If this attribute is set to <code>true</code>, then all results from a stored procedure call that don't have a corresponding <i>SQL parameter definition</i> will be bypassed.

E.g. Stored Procedures may return an update count value, even though your Stored Procedure only declared a single result parameter. The exact behavior depends on the used database.

The value is set on the underlying <code>JdbcTemplate</code>.

Only few developers will probably ever like to process update counts, thus the value defaults to <code>true</code>.

#### Expect single result
This attribute indicates that only one result object shall be returned from the stored procedure/function call. If set to <code>true</code> and the result map from the stored procedure/function call contains only 1 element, then that 1 element is extracted and returned as payload.

If the result map contains more than 1 element and expect single result is <code>true</code>, then a <code>MessagingException</code> is thrown.

Otherwise the complete result map is returned as the payload.

Important Note: Several databases such as H2 are not fully supported for stored procedure and/or function calls.

The H2 database, for example, does not fully support the <code>CallableStatement</code> semantics and when executing function calls against H2, a result list is returned, rather than a single value.

#### Return value required
Indicates the procedure's return value should be included in the results returned.

Default is <code>false</code>.

#### JDBC call operations cache size
Defines the maximum number of cached <code>SimpleJdbcCallOperations</code> instances.

Basically, for each stored procedure name a new <code>SimpleJdbcCallOperations</code> instance is created that in return is being cached.

The default cache size is <code>10</code>. A value of <code>0</code> disables caching.


SQL parameter definitions define the type and value of each parameter.

If you are using a database that is fully supported, you typically don't have to specify the stored procedure parameter definitions.

Instead, those parameters can be automatically derived from the JDBC meta-data. However, if you are using databases that are not fully supported or if you like to provide customized parameter definitions, you can set those parameters explicitly. See also the <i>ignore column meta-data</i> attribute.

Note that the <i>order</i>, <i>name</i>, <i>type</i>, <i>direction</i> and <i>scale</i> of the SQL parameters should <b>exactly match</b> the settings specified on the database.

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

