---
id: string-to-wrapped-xml-transformer
title: String to wrapped XML transformer
sidebar_label: String to wrapped XML transformer
---
#### Payload transformer that transforms a String into a valid XML document.
Payload transformer that transforms the given String into a valid XML document by wrapping it with a root element and setting the string as the (only) text node child of that element.

The result of this transformation will be a complete, well-formed XML document as a String.

#### Root element namespace
Specifies the namespace of the root element wrapping the text content in the resulting XML document.

Default is null, which indicates no namespace.

#### Root element name
Specifies the name that will be used for the root element wrapping the text content in the resulting XML document.

Default when empty: "root"


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
id: string-to-wrapped-xml-transformer
title: String to wrapped XML transformer
sidebar_label: String to wrapped XML transformer
---
#### Payload transformer that transforms a String into a valid XML document.
Payload transformer that transforms the given String into a valid XML document by wrapping it with a root element and setting the string as the (only) text node child of that element.

The result of this transformation will be a complete, well-formed XML document as a String.

#### Root element namespace
Specifies the namespace of the root element wrapping the text content in the resulting XML document.

Default is null, which indicates no namespace.

#### Root element name
Specifies the name that will be used for the root element wrapping the text content in the resulting XML document.

Default when empty: "root"


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

