---
id: channel
title: Channel
sidebar_label: Channel
---
#### Used to transport a message between two endpoints.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-channels-section.html" target="_blank">Documentation</a>


Specifies the interceptors of this channel.

A <i>wire tap</i> can be used to send a copy of the messages of this channel on an other channel, for backup or logging purposes for example.

The <i>entry tracking</i> and <i>exit tracking</i> interceptors are used for message tracking at the first and last channel(s) of a full message flow.

The <i>debug</i> interceptor is used for sending debug messages to the debugger.

#### Datatype
Specifies the datatype of this channel.

Use to create a Datatype Channel that only accepts messages containing  certain payload types. Leave empty if all datatypes are accepted.

Set with a comma-delimited list of the fully-qualified class names of the types, eg.: <i>java.lang.String, java.lang.Number</i>

Default: <i>empty</i>

#### Channel type
Specifies the channel type

1. <b>Direct Channel (default)</b>
Dispatches messages directly to a subscriber. The invocation will occur in the sender's thread. 

2. <b>Queue Channel</b>
Each Message is placed in a BlockingQueue whose capacity may be specified. 
If the queue has reached capacity, then the sender will block until room is available. Likewise, a receive call will return immediately if a message is available on the queue, but if the queue is empty, then a receive call may block until either a message is available or the timeout elapses.

3. <b>RendezvousChannel</b>
A zero-capacity version of QueueChannel. This accommodates "handoff" scenarios (i.e. blocking while waiting for another party to send or receive). 

4. <b>ExecutorChannel</b>
Delegates all dispatching invocations to an Executor. Does not block the sender's Thread since it uses another Thread for the dispatch.

NOTE: unlike DirectChannel, the ExecutorChannel does not support a shared transactional context between sender and handler, because the Executor typically does not block the sender's Thread since it uses another Thread for the dispatch. (SyncTaskExecutor is an exception but would provide no value for this channel. If synchronous dispatching is required, a DirectChannel should be used instead).

#### Fixed subscriber
When <code>true</code>, only one subscriber is allowed; the subscriber must be available at context initialization time, and will be subscribed during bean initialization rather than when being started; "auto-startup" will take no effect on a subscriber to this channel, the subscriber will always be "started". The subscriber cannot be stopped.

Only allowed on a <i>direct channel</i> without a <i>datatype</i>.

Default is <code>false</code>.

#### Capacity
Capacity of the queue channel.

Can <b>not</b> be used when the queue channel is backed by a <i>message store</i>. In this case the capacity should be configured on the <i>message store</i> support object.

Default is unlimited (actually: <code>Integer.MAX_VALUE</code>).


#### Message store
Optional <i>message store</i> to hold the queued messages.

If not set, an in-memory queue is used that does not provide any message persistance.

#### Task executor
TaskExecutor to perform the dispatch.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

