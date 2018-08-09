# JMS listener container
#### A container for hosting JMS message listeners that share the same connection settings.
JMS message listeners are responsible for receiving JMS messages from a specific JMS destination and then processing them.

If you want to receive JMS messages and process them using a normal message flow, use a <i>JMS inbound channel adapter</i> or <i>JMS inbound gateway</i> instead (both are specialized implementations of <i>JMS listener container</i> that are optimized for this specific case).

#### Connection factory
The <i>JMS connection factory</i> for creating connections to the JMS server.

<i>Required</i>

<b>Note</b>: Don't use a <i>caching connection factory</i> in combination with dynamic scaling. Ideally, don't use it with a message listener container at all, since it is generally preferable to let the listener container itself handle appropriate caching within its lifecycle. Also, stopping and restarting a listener container will only work with an independent, locally cached connection - not with an externally cached one.

#### Destination type
The JMS destination type for this listener: <i>queue</i>, <i>topic</i>, <i>durableTopic</i>, <i>sharedTopic</i>, <i>sharedDurableTopic</i>. This enables potentially the <i>pubSubDomain</i>, <i>subscriptionDurable</i> and <i>subscriptionShared</i> properties of the container.

Default is <i>queue</i> (i.e. disabling those 3 properties).


The JMS message listeners hosted in this container.

#### Concurrency
The number of concurrent sessions/consumers to start for each listener. Can either be a simple number indicating the maximum number (e.g. <code>5</code>) or a range indicating the lower as well as the upper limit (e.g. <code>3-5</code>). Note that a specified minimum is just a hint and might be ignored at runtime.

Keep concurrency limited to 1 in case of a topic listener or if message ordering is important; consider raising it for general queues.

Default is <code>1</code>.

#### Acknowledge
JMS acknowledge modes:
- <b>Auto</b> (default): automatic message acknowledgment <i>before</i> listener execution; no redelivery in case of exception thrown.
- <b>Client</b>: automatic message acknowledgment <i>after</i> successful listener execution; no redelivery in case of exception thrown.
- <b>Dups-ok</b>: <i>lazy</i> message acknowledgment during or after listener execution; <i>potential redelivery</i> in case of exception thrown.
- <b>Transacted</b>: transactional acknowledgment after successful listener execution; <i>guaranteed redelivery</i> in case of exception thrown.

#### Message converter
A reference to the <i>message converter</i> strategy for converting JMS messages to listener method arguments.

Default is a <code>SimpleMessageConverter</code>.

#### Task executor
A reference to a <i>task executor</i> for executing JMS listener invokers.

Default is a <code>SimpleAsyncTaskExecutor</code> using internally managed threads.

#### Response destination type
The JMS destination type for responses: <i>queue</i> or <i>topic</i>.

Default is the value of the <i>destination-type</i> attribute.

#### Client ID
The JMS client ID for this listener container.

Needs to be specified when using subscriptions.

#### Cache
The cache level for JMS resources (<i>none</i>, <i>connection</i>, <i>session</i>, <i>consumer</i> or <i>auto</i>).

By default (<i>auto</i>) the cache level will effectively be <i>consumer</i>, unless an external transaction manager has been specified in which case the effective default will be <i>none</i> (assuming J2EE-style transaction management where the given connection factory is an XA-aware pool).

#### Prefetch
The maximum number of messages to load into a single session.

Note that raising this number might lead to starvation of concurrent consumers!

#### Recovery interval
Specify the interval between recovery attempts, in milliseconds.

Default is <code>5000</code> ms (5 seconds).

#### Receive timeout
The timeout (in milliseconds) to use for receive calls; <code>-1</code> indicates no timeout at all.

Default is <code>1000</code> (1 second).

