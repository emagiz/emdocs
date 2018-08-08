
Routes messages to a channel based on a value in the header.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-routing-chapter.html#router-implementations-headervaluerouter" target="_blank">Documentation</a>

The <i>header name</i> attribute specifies which
 header value to lookup. That header value can then provide the name of a
 channel to be resolved. Alternatively, 1 or more 'mapping' sub-elements
 may be provided with expected header values mapped to channels.


Header name
Name of the header whose value to use.

Examples:
busname_messageType
busname_sourceSystem

<i>Required</i>


Maps values of the message header to channels.

If the value is not found in a mapping, the router will look for a channel which name matches the value.

Note that if the header contains multiple values (comma-separated string or a string array), this router will route the message to multiple channels (this duplicates the message).


Resolution required
If set to <i>true</i> and channel resolution fails, a <code>MessageDeliveryException</code> is thrown. If set to <i>false</i> such failures are (silently) ignored, possibly resulting in the router resolving zero channels.

Channel resolution failure means that the routing criteria cannot be successfully resolved, for example when a <i>header value router</i> tries to route a message with a header value that is not specified in the mappings, or when any of the XPath evaluation results of an <i>XPath router</i> cannot be found in the mappings.

Note that this behaviour does <b>not</b> apply to cases where resolving the routing criteria (successfully) results in zero channels, for example when a <i>header value router</i> tries to route a message that doesn't contain the specified message header, or when the evaluation of the XPath expression by an <i>XPath router</i> produces no results.

Please be aware that instead of suppressing these exceptions, it is also possible to explicitly drop certain messages by routing them to the <i>nullChannel</i>.

Default is <i>true</i>.


Ignore send failures
If set to <i>true</i>, failures to send to a message channel will be ignored. If set to <i>false</i>, a <code>MessageDeliveryException</code> will be thrown instead, and if the router resolves more than one channel, any subsequent channels will not receive the message.

Please be aware that when using direct channels (single threaded), send-failures can be caused by exceptions thrown by components much further down-stream.

Also note that this behaviour does <b>not</b> apply to the the optional <i>default output channel</i>.

Default is <i>false</i>.


Default output channel
The default channel where messages should be sent if the router didn't send the message to any of the normal output channels.

If no default output channel is provided and the router didn't send the message to any of the normal output channels a <code>MessageDeliveryException</code> is thrown. If you would like to silently drop those messages instead, use the <i>nullChannel</i> as the default output channel.


A router might not be able to send a message to any of the normal output channels in the following cases:

<b><i>resolving the routing criteria resulted in zero channels</i></b>
For example, when a <i>header value router</i> tries to route a message that doesn't contain the specified message header, or when the evaluation of the XPath expression by an <i>XPath router</i> produces no results.

<b><i>resolving the routing criteria failed and 'resolution required' is disabled</i></b>
For example, when a <i>header value router</i> tries to route a message with a header value that is not specified in the mappings, or when all results of the evaluation of the XPath expression by an <i>XPath router</i> cannot be found in the mappings.

<b><i>all send attempts failed and 'ignore send failures' is enabled</i></b>
For example, when every normal output channel connects to a down-stream filter that rejects the message using the <i>throw exception on rejection</i> option (the "selective consumer" pattern).


Apply sequence
Specify whether sequence number and size headers should be added to each message.

Default is <i>false</i>.


Timeout
Specify the maximum amount of time in milliseconds to wait when sending messages to the target message channels.

By default the send will block indefinitely.


Id
Name that uniquely identifies this flow component.

<i>Required</i>


Input channel
Channel to consume the input messages from.

<i>Required</i>

