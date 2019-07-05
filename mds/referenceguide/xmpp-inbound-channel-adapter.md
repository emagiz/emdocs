---
id: xmpp-inbound-channel-adapter
title: XMPP inbound channel adapter
sidebar_label: XMPP inbound channel adapter
---
#### Receives chat messages sent to a given account.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xmpp.html#xmpp-message-inbound-channel-adapter" target="_blank">Documentation</a>

Configures an endpoint that will receive chat messages sent to a given account and then forward those messages to a MessageChannel.

#### Payload expression
A SpEL expression to evaluate a <i>payload</i> with the incoming <code>org.jivesoftware.smack.packet.Message</code> as root object. Useful in case of custom (XEP) XMPP interactions, e.g. GCM.

By default a message <i>body</i> is used as <i>payload</i>. The <code>#extension</code> SpEL variable is registered in the evaluation context if one and only one extension is present in the message.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this adapter's invocation.

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

