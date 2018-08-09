# JMS listener
#### Receives JMS messages from a specific JMS destination and processes them.
JMS message listeners are responsible for receiving JMS messages from a specific JMS destination and then processing them.

If you want to receive JMS messages and process them using a normal message flow, use a <i>JMS inbound channel adapter</i> or <i>JMS inbound gateway</i> instead (both are specialized implementations of <i>JMS listener container</i> that are optimized for this specific case).

#### Destination
The destination name for this listener (a JMS <i>queue</i>, <i>topic</i> or <i>durable topic</i>).

<i>Required</i>

#### Message listener
The JMS message listener implementation that will handle incoming JMS messages.

<i>Required</i>

#### Selector
A JMS message selector boolean expression that evaluates the headers of the messages. Only the messages where this expression evaluates to <code>true</code> are received.

See the java JMS specification for message selector syntax:
<a href="http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html" target="_blank">http://download.oracle.com/javaee/1.4/api/javax/jms/Message.html</a>

#### Response destination
The name of the default response destination to send response messages to. This will be applied in case of a request message that does not carry a <code>JMSReplyTo</code> field. The type of this destination will be determined by the listener container's <i>response destination type</i> setting.

Note: this only applies to a listener method with a return value, for which each result object will be converted into a response message.

#### Subscription
The name for the durable subscription, if any.

#### Concurrency
The number of concurrent sessions/consumers to start for this listener. Can either be a simple number indicating the maximum number (e.g. <code>5</code>) or a range indicating the lower as well as the upper limit (e.g. <code>3-5</code>). Note that a specified minimum is just a hint and might be ignored at runtime.

Default is the value provided by the container.

