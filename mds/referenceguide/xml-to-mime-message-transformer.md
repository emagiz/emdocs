---
id: xml-to-mime-message-transformer
title: XML to MIME message transformer
sidebar_label: XML to MIME message transformer
---
#### Payload transformer that transforms an XML message to a Mime Mail Message. 
The payload of the incoming message must be a <code>&lt;mail:SendMailRequest&gt;</code>, as defined by the XML schema located at: 
<code>classpath:com/emagiz/components/mail/emagiz-mail-1.0.xsd.</code>


#### Mail sender
Reference to a mail sender that prepares the MIME message.

Note: The 'send' functionality of the 'sender' is not used in this case, only the preparation of the message.


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

