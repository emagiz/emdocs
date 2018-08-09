
An event-driven adapter that receives logging events of the application.
A message producer endpoint that registers itself as an <code>Appender</code> for <i>Logback</i>, sending all received logging events as XML messages to the output channel.

Note that any downstream logging events caused by the sending of logging messages are automatically skipped by <i>Logback</i> appenders as long as these are <b>send from the same thread</b>. This means that when the message flow this adapter is connected to is not single-threaded (e.g., by using a <i>queue-channel</i>), this will cause an infinite loop! To prevent this, try to avoid any downstream logging where possible and make sure the entire message flow is single-threaded (by using <i>direct-channels</i>, for example).

The generated messages will be complete, well-formed XML documents represented as a String. These messages will contain one <code>&lt;logging-event&gt;</code> element, as defined by the XML schema located at:
<code>classpath:com/emagiz/components/logging/emagiz-logging-1.0.xsd</code>


Logger name
Sets the name of the <code>Logger</code> this adapter will be appended to in order to receive logging events.

If not set, the root logger is used by default.


Level
Sets the logging level below which logging events will be filtered out by this appender.

Note that this setting is independent of the log level of the <code>Logger</code>, and will only appear to have an effect when it is set to a higher level than the <code>Logger</code>. In general, if you're not interested at all in certain log levels you should use the level of the <code>Logger</code>, as this will generate less logging events (better performance). Change the log level of this appender when you want different log levels for multiple appenders. 

If not set, the level is <i>INFO</i> by default (filtering out any <i>TRACE</i> and <i>DEBUG</i> events).


Appender type
Sets the type of appender this message producer endpoint will register itself as.

 - <b>UNSYNCHRONISED</b>: An unsynchronised appender could improve performance, but can also cause thread synchronisation issues in the downstream message flow.
 - <b>SYNCHRONISED</b>: A synchronised appender could prevent any thread synchronisation issues in the downstream message flow, but can also decrease performance.
 - <b>ASYNCHRONOUS</b>: An asynchronous appender could prevent any thread synchronisation issues in the downstream message flow and <i>significantly</i> improve performance by decoupling application threads and logging appenders, but can also lead to loss of logging events and more heap memory usage because it will queue events in memory. Also when this queue is full, application threads will block until the queue is no longer at its maximum capacity.

Default is <code>UNSYNCHRONISED</code>.


Queue size
The maximum capacity of the blocking queue.

Default is <code>256</code>.


Discarding threshold
The threshold to start discarding messages when the blocking queue is filling up. By default, when the blocking queue has 20% capacity remaining, it will drop events of level <i>TRACE</i>, <i>DEBUG</i> and <i>INFO</i>, keeping only events of level <i>WARN</i> and <i>ERROR</i>.

Setting the threshold to <code>0</code> disables any discarding of logging events; setting the threshold to the maximum queue size (or higher) will result in all logging events of level <i>TRACE</i>, <i>DEBUG</i> and <i>INFO</i> being discarded immediately.

Default is 20% of the queue size.


Retry interval
If sending a logging event to the output channel fails, this appender is stopped automatically to prevent a cascading failure. By specifying a <i>retry interval</i>, this appender will schedule tasks to periodically try to startup again. All logging events that were logged in the mean time will be lost however.

Default is <i>undefined</i>, disabling any retry attempts.


Cache max size
To detect and aggregate repeating log entries, this channel adapter uses an internal cache to keep track of the most recent log messages. This setting can be used to change the maximum number of log entries that are kept in memory, or even completely disable the detection of repeating log entries by using a value less than <code>1</code>.

Default is <code>100</code>.


Cache check interval
To detect and aggregate repeating log entries, this channel adapter uses an internal cache to keep track of the most recent log messages. A cleanup task periodically runs to check for log entries that should be moved out of the cache and send to the output channel. This setting can be used to change the interval (in milliseconds) between these cleanup tasks.

Default is <code>60000</code> (1 minute).


Cache max repeat count
To detect and aggregate repeating log entries, this channel adapter uses an internal cache to keep track of the most recent log messages. A cleanup task periodically runs to check for log entries that should be moved out of the cache and send to the output channel. This setting can be used to change the number of repeats after which a log entry will be moved out of the cache, regardless of whether it is still repeating.

Default is <code>1000</code>.


Cache max repeat delay
To detect and aggregate repeating log entries, this channel adapter uses an internal cache to keep track of the most recent log messages. A cleanup task periodically runs to check for log entries that should be moved out of the cache and send to the output channel. This setting can be used to change the maximum delay (in milliseconds) between two similar log entries to classify them as "repeating". After this delay has passed without another identical message being logged, a log entry will be moved out of the cache since it is no longer considered to be repeating.

Default is <code>120000</code> (2 minutes).


Send timeout
The maximum amount of time in milliseconds to wait when sending a message to the output channel.

Default is <code>0</code>, i.e. sends should be handled immediately without blocking waits.


Error channel
If a (synchronous) downstream exception is thrown and an error channel is specified, the <code>MessagingException</code> will be sent to this channel. Otherwise, any such exception will simply be logged as a warning by the channel adapter.


Id
Name that uniquely identifies this flow component.

<i>Required</i>


Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

