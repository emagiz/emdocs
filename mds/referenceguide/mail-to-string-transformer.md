---
id: mail-to-string-transformer
title: Mail to string transformer
sidebar_label: Mail to string transformer
---
#### Transforms a mail message to a string message
Transforms a Message payload of type Message to a String. 

If the mail message's content is a String, it will be the payload of the result Message. If the content is a Multipart, a String will be created from an output stream of bytes using the provided charset (or UTF-8 by default). 

#### Charset
Character set to be used for the string output.

Default used when empty: UTF-8

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
id: mail-to-string-transformer
title: Mail to string transformer
sidebar_label: Mail to string transformer
---
#### Transforms a mail message to a string message
Transforms a Message payload of type Message to a String. 

If the mail message's content is a String, it will be the payload of the result Message. If the content is a Multipart, a String will be created from an output stream of bytes using the provided charset (or UTF-8 by default). 

#### Charset
Character set to be used for the string output.

Default used when empty: UTF-8

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

