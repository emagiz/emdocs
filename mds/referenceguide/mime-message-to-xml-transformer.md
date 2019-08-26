---
id: mime-message-to-xml-transformer
title: MIME message to XML transformer
sidebar_label: MIME message to XML transformer
---
#### Payload transformer that converts MIME messages to XML. 
Transformer that converts the MIME string messages to XML.

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is a 'mime-message' element as defined by the XML schema located at:
<i>classpath:com/emagiz/components/mail/emagiz-mail-1.0.xsd</i> 

Note that this transformer only supports MIME messages that can successfully be mapped to such an XML document. For example, the message can at most contain 1 MIME part with Content-Type <code>text/plain</code> and 1 MIME part with Content-Type <code>text/html</code>, because these are mapped to the <code>&lt;text-content&gt;</code> and <code>&lt;html-content&gt;</code> XML elements.

#### Result type
Sets the result type (<code>XomDocument</code>, <code>DomDocument</code> or <code>String</code>) for the transformation. 

Default is <code>String</code>.


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

---
id: mime-message-to-xml-transformer
title: MIME message to XML transformer
sidebar_label: MIME message to XML transformer
---
#### Payload transformer that converts MIME messages to XML. 
Transformer that converts the MIME string messages to XML.

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is a 'mime-message' element as defined by the XML schema located at:
<i>classpath:com/emagiz/components/mail/emagiz-mail-1.0.xsd</i> 

Note that this transformer only supports MIME messages that can successfully be mapped to such an XML document. For example, the message can at most contain 1 MIME part with Content-Type <code>text/plain</code> and 1 MIME part with Content-Type <code>text/html</code>, because these are mapped to the <code>&lt;text-content&gt;</code> and <code>&lt;html-content&gt;</code> XML elements.

#### Result type
Sets the result type (<code>XomDocument</code>, <code>DomDocument</code> or <code>String</code>) for the transformation. 

Default is <code>String</code>.


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

