# Address settings
Artemis has a unique addressing model that is both powerful and flexible and that offers great performance. The addressing model comprises three main concepts: addresses, queues and routing types.

An address represents a messaging endpoint. Within the configuration, a typical address is given a unique name, 0 or more queues, and a routing type.

A queue is associated with an address. There can be multiple queues per address. Once an incoming message is matched to an address, the message will be sent on to one or more of its queues, depending on the routing type configured. Queues can be configured to be automatically created and deleted.

<a href="https://activemq.apache.org/artemis/docs/latest/address-model.html" target="_blank">Documentation</a>

## Match
A wildcard expression contains words delimited by the character <code>.</code> (full stop).

The special characters <code>#</code> and <code>*</code> also have special meaning and can take the place of a word:
- the character <code>#</code> matches any sequence of zero or more words
- the character <code>*</code> matches a single word

So the wildcard <code>news.europe.#</code> would match <code>news.europe</code>, <code>news.europe.sport</code>, <code>news.europe.politics</code> and <code>news.europe.politics.regional</code>, but would not match <code>news.usa</code>, <code>news.usa.sport</code> nor <code>entertainment</code>.

The wildcard <code>news.*</code> would match <code>news.europe</code>, but not <code>news.europe.sport</code>.

The wildcard <code>news.*.sport</code> would match <code>news.europe.sport</code> and also <code>news.usa.sport</code>, but not <code>news.europe.politics</code>.

<i>Required</i>

## Auto create queues
Whether or not the broker should automatically create a queue when a message is sent or a consumer tries to connect to a queue whose name fits the address match. Queues which are auto-created are durable, non-temporary, and non-transient.

Default is <i>Yes</i>.

Auto delete queues
Whether or not the broker should automatically delete auto-created queues when they have both 0 consumers and 0 messages.

Default is <i>Yes</i>.

Delete queues on restart
How the broker should handle queues deleted on configuration reload. This delete policy can be set to <i>Off</i> or <i>Force</i>.

Default is <i>Off</i>.

Auto create addresses
When set to true, the broker will create the address requested by the client if it does not exist already.

The default is <i>Yes</i>.

Auto delete addresses
When set to true, the broker will be delete any auto-created address once all of it’s queues have been deleted.

The default is <i>Yes</i>.

Delete addresses on restart
How the broker should handle addresses deleted on configuration reload. This delete policy can be set to <i>Off</i> or <i>Force</i>.

Default is <i>Off</i>.

Max consumers
The max-consumers parameter of a queue element can be used to limit the number of connected consumers allowed at any one time. 

Default value is <code>-1</code> (disabled).

Purge on no consumers
If a user requires to pre-create a queue that behaves like a non-durable subscription queue the purge-on-no-consumers flag can be enabled on the queue.

When purge-on-no-consumers is set to <i>Yes</i> the queue will not start receiving messages until a consumer is attached. When the last consumer is detached from the queue. The queue is purged (it's messages are removed) and will not receive any more messages until a new consumer is attached.

Default is <i>No</i>.

Queue routing type
A routing type determines how messages are sent to the queues associated with an address. An Apache ActiveMQ Artemis address can be configured with two different routing types. Possible values are <i>Multicast</i> and <i>Anycast</i>.

Default value is <i>Multicast</i>.

Address routing type
A routing type determines how messages are sent to the queues associated with an address. An Artemis address can be configured with two different routing types. Possible values are <i>Multicast</i> and <i>Anycast</i>.

Default value is <i>Multicast</i>.

Last value queue
Defines whether a queue only uses last values or not.

Last value queues are special queues which discard any messages when a newer message with the same value for a well-defined last value property is put in the queue. In other words, a last value queue only retains the last value.

The property name used to identify the last value is <code>_AMQ_LVQ_NAME</code>.

Default is <i>No</i>.

Exclusive queue
Exclusive queues are special queues which route all messages to only one consumer at a time. This is useful when you want all messages to be processed serially by the same consumer, when a producer does not specify Message Grouping.

An example might be orders sent to an address and you need to consume them in the exact same order they were produced.

Obviously exclusive queues have a draw back that you cannot scale out the consumers to improve consumption as only one consumer would technically be active. Here we advise that you look at message groups first.

Default is <i>No</i>.

Max memory size
The maximum memory the address could have before applying the <i>address full message policy</i>.

No that this setting applies <b>per address</b>. If you configure a maximum size for an address, that means each matching address will have the maximum size that you specified. It <b>does not</b> mean that the total <b>overall size</b> of all matching addresses is limited to this size.

Default is <code>-1</code> (no limit).

Address full message policy
This attribute can have one of the following values: <i>Page</i>, <i>Drop</i>, <i>Fail</i> or <i>Block</i> and determines what happens when an address where max memory size is specified becomes full.

If the value is <i>Page</i> then further messages will be paged to disk. If the value is <i>Drop</i> then further messages will be silently dropped. If the value is <i>Fail</i> then further messages will be dropped and an exception will be thrown on the client-side. If the value is <i>Block</i> then client message producers will block when they try and send further messages.

Default is <i>Page</i>.

Page size
Messages are stored per address on the file system. Each address has an individual folder where messages are stored in multiple files (page files). Each file will contain messages up to the configured <i>Page size</i>. The system will navigate on the files as needed, and it will remove the page file as soon as all the messages are acknowledged up to that point.

The <i>Page size</i> must be (significantly) smaller than the <i>Max memory size</i>.

Default is <code>10485760</code> bytes (10 MiB).

Max size page cache 
The system will keep up to this amount of page files in memory to optimize IO during paging navigation.

Default is <code>5</code>.

Max size reject threshold
Used with the address full 'Block' policy, the maximum size (in bytes) an address can reach before messages start getting rejected. Works in combination with max-size-bytes for AMQP protocol only. Default = -1 (no limit).

Max delivery attempts
Defines how many time a cancelled message can be redelivered before sending it to the dead letter address (DLA). Set it to <code>-1</code> for infinite redeliveries.

If a DLA is not specified, messages will removed after max-delivery-attempts unsuccessful attempts. 

Default is <code>10</code>.

Redelivery delay
Defines how long to wait (in milliseconds) before attempting redelivery of a cancelled message.

Default is <code>0</code> (no delay between redelivery attempts).

Redelivery multiplier
Multiplier to apply to the time since the last redelivery attempt to compute the time to the next attempt. This allows you to implement an exponential backoff between redelivery attempts.

Default is <code>1.0</code>, resulting in a fixed delay between redelivery attempts.

Max redelivery delay
Maximum value for the <i>redelivery delay</i>, i.e. this limits how much the delay can increase when using a multiplier that is bigger than <code>1.0</code>.

Default is <i>10 * redelivery delay</i>.

Dead letter address
Defines where to send a message that cannot be delivered.

If a dead letter address is not specified, messages will be removed after <i>max delivery attempts</i> unsuccessful attempts.

Default is empty.

Expiry address
Defines where to send a message that has expired.

If messages are expired and no expiry address is specified, messages are simply removed from the queue and dropped.

Default is empty.

Expiry delay
Defines the expiration time that will be used for messages which are using the default expiration time (i.e. <code>0</code>).

For example, if <i>expiry delay</i> is set to <code>10</code> and a message which is using the default expiration time (i.e. <code>0</code>) arrives, then its expiration time of <code>0</code> will be changed to <code>10</code>. However, if a message which is using an expiration time of <code>20</code> arrives, then its expiration time will remain unchanged.

Setting expiry-delay to <code>-1</code> will disable this feature.

Default is <code>-1</code>.

Redistribution delay
Defines the delay in milliseconds after the last consumer is closed on a queue before redistributing messages from that queue to other nodes of the cluster which do have matching consumers. A delay of zero means the messages will be immediately redistributed. A value of <code>-1</code> signifies that messages will never be redistributed.

It often makes sense to introduce a delay before redistributing as it's a common case that a consumer closes but another one quickly is created on the same queue, in such a case you probably don't want to redistribute immediately since the new consumer will arrive shortly.

Default is <code>-1</code> (no redistribution).

Send to DLA on no route
If a message is sent to an address, but the server does not route it to any queues, for example, there might be no queues bound to that address, or none of the queues have filters that match, then normally that message would be discarded.

However if this parameter is set to <i>Yes</i> for that address, if the message is not routed to any queues it will instead be sent to the dead letter address (DLA) for that address, if it exists.

Default is <i>No</i>.

Message counter history limit
How many days to keep message counter history.

Default is <code>10</code> days.

Queue prefetch
The prefetch limit limits the maximum number of messages that can be dispatched to an individual consumer at once. The consumer in turn uses the prefetch limit to size its prefetch message buffer. 

Default is <code>1000</code>.

Management browse page size
How many messages a management resource can browse.

Default is <code>200</code>.

Slow consumer threshold
The minimum rate of message consumption allowed before a consumer is considered "slow." Measured in messages-per-second.

Default is <code>-1</code> (i.e. disabled).

Slow consumer policy
What should happen when a slow consumer is detected.

<i>Kill</i> will kill the consumer's connection (which will obviously impact any other client threads using that same connection).

<i>Notify</i> will send a <code>CONSUMER_SLOW</code> management notification which an application could receive and take action with.

Default is <i>Notify</i>.

Slow consumer check period
How often to check for slow consumers on a particular queue. Measured in seconds.

Default is <code>5</code> seconds.


Configuration settings that are applied on the address level.
A block of settings which will be applied against any addresses with a name that matches a certain wildcard expression.

When <i>match</i> is <code>jms.queue.example</code> for example, the settings would only be applied to any addresses which exactly match the address <code>jms.queue.example</code>. You can also use wildcards to apply settings against many addresses. For example, if you used the match string <code>jms.queue.#</code>, the settings would be applied to all addresses that start with <code>jms.queue.</code> (which would be all JMS queues).

Note that only the most specific match is applied for each address. Some examples from most specific to least specific: <code>jms.queue.example</code> (matches one JMS queue), <code>jms.*.example</code> (matches one JMS queue and one JMS topic), <code>jms.queue.#</code> (matches all JMS queues), <code>jms.#</code> (matches all JMS queues and JMS topics).


Match
A HornetQ wildcard expression contains words delimited by the character <code>.</code> (full stop).

The special characters <code>#</code> and <code>*</code> also have special meaning and can take the place of a word:
- the character <code>#</code> matches any sequence of zero or more words
- the character <code>*</code> matches a single word

So the wildcard <code>news.europe.#</code> would match <code>news.europe</code>, <code>news.europe.sport</code>, <code>news.europe.politics</code> and <code>news.europe.politics.regional</code>, but would not match <code>news.usa</code>, <code>news.usa.sport</code> nor <code>entertainment</code>.

The wildcard <code>news.*</code> would match <code>news.europe</code>, but not <code>news.europe.sport</code>.

The wildcard <code>news.*.sport</code> would match <code>news.europe.sport</code> and also <code>news.usa.sport</code>, but not <code>news.europe.politics</code>.

Note that addresses of JMS queues are always prefixed with <code>jms.queue.</code> and addresses of JMS topics with <code>jms.topic.</code>. So the wildcard <code>jms.queue.#</code> would match all JMS queues for example.

<i>Required</i>


Last value queue
Defines whether a queue only uses last values or not.

Last value queues are special queues which discard any messages when a newer message with the same value for a well-defined last value property is put in the queue. In other words, a last value queue only retains the last value.

The property name used to identify the last value is <code>_HQ_LVQ_NAME</code>.

Default is <i>false</i>.


Max size
The maximum memory the address could have before applying the <i>address full message policy</i>.

No that this setting applies <b>per address</b>. If you configure a maximum size for an address, that means each matching address will have the maximum size that you specified. It <b>does not</b> mean that the total <b>overall size</b> of all matching addresses is limited to this size.

Default is <code>-1</code> (no limit).


Address full message policy
This attribute can have one of the following values: <i>page</i>, <i>drop</i> or <i>block</i> and determines what happens when an address reaches its maximum size.

If the value is <i>page</i> then further messages will be paged to disk. If the value is <i>drop</i> then further messages will be silently dropped. If the value is <i>block</i> then client message producers will block when they try and send further messages.

Default is <i>page</i>.


Page size
The size of each page file used on the paging system.

The page size must be (significantly) smaller than the max size.

Default is <code>10485760</code> (10 MiB)


Page cache max size
The system will keep up to this amount of page files in memory to optimize IO during paging navigation.

Default is <code>5</code>.


Max delivery attempts
Defines how many time a cancelled message can be redelivered before sending to the <i>dead letter address</i>.

Default is <code>10</code>.


Redelivery delay
Defines how long to wait before attempting redelivery of a cancelled message.

Default is <code>0</code> (no delay between redelivery attempts).


Redelivery multiplier
Multiplier to apply to the time since the last redelivery attempt to compute the time to the next attempt. This allows you to implement an exponential backoff between redelivery attempts.

Default is <code>1.0</code>, resulting in a fixed delay between redelivery attempts.


Max redelivery delay
Maximum value for the <i>redelivery delay</i>, i.e. this limits how much the delay can increase when using a multiplier that is bigger than <code>1.0</code>.

Default is equal to the <i>redelivery delay</i>.


Dead letter address
Defines where to send a message that cannot be delivered.

If a dead letter address is not specified, messages will be removed after <i>max delivery attempts</i> unsuccessful attempts.

Default is empty.


Expiry delay
Defines the expiration time that will be used for messages which are using the default expiration time (i.e. <code>0</code>).

For example, if <i>expiry delay</i> is set to <code>10</code> and a message which is using the default expiration time (i.e. <code>0</code>) arrives, then its expiration time of <code>0</code> will be changed to <code>10</code>. However, if a message which is using an expiration time of <code>20</code> arrives, then its expiration time will remain unchanged.

Setting expiry-delay to <code>-1</code> will disable this feature.

Default is <code>-1</code>.


Expiry address
Defines where to send a message that has expired.

If messages are expired and no expiry address is specified, messages are simply removed from the queue and dropped.

Default is empty.


Redistribution delay
Defines the delay in milliseconds after the last consumer is closed on a queue before redistributing messages from that queue to other nodes of the cluster which do have matching consumers. A delay of zero means the messages will be immediately redistributed. A value of <code>-1</code> signifies that messages will never be redistributed.

It often makes sense to introduce a delay before redistributing as it's a common case that a consumer closes but another one quickly is created on the same queue, in such a case you probably don't want to redistribute immediately since the new consumer will arrive shortly.

Default is <code>-1</code> (no redistribution).


Send to DLA on no route
If a message is sent to an address, but the server does not route it to any queues, for example, there might be no queues bound to that address, or none of the queues have filters that match, then normally that message would be discarded. However if this parameter is set to true for that address, if the message is not routed to any queues it will instead be sent to the dead letter address (DLA) for that address, if it exists.

Default is <i>false</i>.


Message counter history limit
How many days to keep message counter history.

Default is <code>0</code>.


A slow consumer with a server-side queue (e.g. JMS topic subscriber) can pose a significant problem for broker performance. If messages build up in the consumer's server-side queue then memory will begin filling up and the broker may enter paging mode which would impact performance negatively. However, criteria can be set so that consumers which don't acknowledge messages quickly enough can potentially be disconnected from the broker which in the case of a non-durable JMS subscriber would allow the broker to remove the subscription and all of its messages freeing up valuable server resources.

By default the server will not detect slow consumers.

The calculation to determine whether or not a consumer is slow only inspects the number of messages a particular consumer has <i>acknowledged</i>. It doesn't take into account whether or not flow control has been enabled on the consumer, whether or not the consumer is streaming a large message, etc. The message production rate is also assumed to meet or exceed the slow consumer threshold. Keep this in mind when configuring slow consumer detection.

Please note that slow consumer checks are performed using the scheduled thread pool and that each queue on the broker with slow consumer detection enabled will cause a new entry in the internal <code>java.util.concurrent.ScheduledThreadPoolExecutor</code> instance. If there are a high number of queues and the <i>slow consumer check period</i> is relatively low then there may be delays in executing some of the checks. However, this will not impact the accuracy of the calculations used by the detection algorithm.


Slow consumer threshold
The minimum rate of message consumption allowed before a consumer is considered "slow." Measured in messages-per-second.

Default is <code>-1</code> (i.e. disabled).


Slow consumer policy
What should happen when a slow consumer is detected.

<i>Kill</i> will kill the consumer's connection (which will obviously impact any other client threads using that same connection).

<i>Notify</i> will send a <code>CONSUMER_SLOW</code> management notification which an application could receive and take action with.

Default is <i>notify</i>.


Slow consumer check period
How often to check for slow consumers on a particular queue. Measured in seconds.

Default is <code>5</code>.

