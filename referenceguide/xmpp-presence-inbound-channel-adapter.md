# XMPP presence inbound channel adapter
#### Receives presence states over a XMPP connection.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xmpp.html#xmpp-roster-inbound-channel-adapter" target="_blank">Documentation</a>

Configures an endpoint that will forward Presence state changes to a MessageChannel.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this adapter's invocation.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

