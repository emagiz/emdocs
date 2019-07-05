---
id: xmpp-header-enricher
title: XMPP header enricher
sidebar_label: XMPP header enricher
---
#### Adds XMPP headers to a message.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xmpp.html#xmpp-message-outbound-channel-adapter" target="_blank">Documentation</a>

When sending chat messages to other users on XMPP using the Outbound Message Channel Adapter, the XMPP headers of the messages are used. 

The adapter expects as its input - at a minimum - a String payload, and a header value for 'CHAT_TO' that specifies to which user the Message should be sent. 

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

