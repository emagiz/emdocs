---
id: object-to-string-transformer
title: Object to string transformer
sidebar_label: Object to string transformer
---
#### Transformer that converts any message payload to a string payload.
A simple transformer that creates an outbound payload by invoking the inbound payload's <code>toString()</code> method, unless the payload is a <code>byte[]</code> or <code>char[]</code>.

If the payload is a <code>byte[]</code>, it will be transformed to a string containing the array's contents, using the <i>charset</i> which by default is <code>UTF-8</code>.

If the payload is a <code>char[]</code>, it will be transformed to a string object with the array's contents.

#### Charset
Specify the charset (e.g., <code>US-ASCII</code>, <code>ISO-8859-1</code>, <code>UTF-8</code>) to be used when transforming <code>byte[]</code> payloads. When transforming any other type of payload this setting has no effect.

Default is <code>UTF-8</code>.

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

