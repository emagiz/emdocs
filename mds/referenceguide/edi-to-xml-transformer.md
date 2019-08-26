---
id: edi-to-xml-transformer
title: EDI to XML transformer
sidebar_label: EDI to XML transformer
---
#### Transforms EDI messages into one or more XML messages
Transformer that uses <i>Smooks</i> for converting EDI messages into one or more XML documents.

Supports the following message payload types for the EDI content:
- <code>String</code>
- <code>byte[]</code>
- <code>File</code> *
- <code>InputStream</code> *
- <code>Reader</code> *
- <code>StreamSource</code> *

The resulting XML documents will always be returned as a <code>String</code> value.

*: Note that this transformer is capable of processing huge message streams by splitting them into a series of many smaller messages: to achieve this specify a <i>target selector</i> on the advanced tab.

#### EDI mapping
The EDI mapping file specifying the format of the request messages.

<i>Required</i>

#### Delete files
Specify whether to delete the source file after a (successful) transformation.

When set to <i>true</i>, it will only have an effect if the inbound message has a <code>File</code> payload or a <code>file_originalFile</code> header value containing either a <code>File</code> instance or a <code>String</code> representing the original file path. 

Default is <i>false</i>.

#### Validate
Whether to perform data validation when processing the EDI content.

Note this validation only applies to the <b>contents</b> of fields/components/subcomponents that have one or more of the following settings specified: <i>data type</i>, <i>min length</i> or <i>max length</i>. The <b>structure</b> of the message is always validated during processing, irregardless of this setting.

Default is <i>false</i>.

#### Ignore new lines
Whether to ignore "unexpected" new lines in the EDI content (i.e. new lines not immediately following the end of a segment).

Default is <i>false</i>.

#### Charset
Character set to be used to decode the bytes of the incoming message into (readable) text. If the payload of the incoming message is already in "text form" (i.e. a <code>String</code>, <code>Reader</code> or <code>StreamSource</code>), this property is not used. 

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)

#### Target selector
Smooks selector expression for splitting the EDI message stream into fragments for the output XML messages.

Default is <code>$document</code>, which results in the entire incoming EDI message stream being transformed into a single XML message.

#### Selector namespace
Optional XML namespace for the selector expression.

If specified, XML elements will only match the <i>target selector</i> expression if they have the exact same namespace. If not specified (the default), the namespace is ignored when matching XML elements to the <i>target selector</i> expression.

#### Requires reply
Whether this transformer must send at least one message to the output channel for each incoming message. If enabled and an incoming message doesn't result in at least one outgoing message, a <code>ReplyRequiredException</code> is thrown instead. 

Default is <i>true</i>.

#### Apply sequence
Whether to add the sequence headers (<code>correlationId</code>, <code>sequenceNumber</code> and <code>sequenceSize</code>) to the output messages.

Note that because of the streaming nature of this transformer, the correct value for the <code>sequenceSize</code> header cannot be determined when sending the output messages: value <code>-1</code> is used instead.

Default is <i>false</i>.

#### Send timeout
Set the timeout (in milliseconds) for sending messages to the output channel. 

Default is <code>-1</code>, i.e. wait indefinitely.

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
id: edi-to-xml-transformer
title: EDI to XML transformer
sidebar_label: EDI to XML transformer
---
#### Transforms EDI messages into one or more XML messages
Transformer that uses <i>Smooks</i> for converting EDI messages into one or more XML documents.

Supports the following message payload types for the EDI content:
- <code>String</code>
- <code>byte[]</code>
- <code>File</code> *
- <code>InputStream</code> *
- <code>Reader</code> *
- <code>StreamSource</code> *

The resulting XML documents will always be returned as a <code>String</code> value.

*: Note that this transformer is capable of processing huge message streams by splitting them into a series of many smaller messages: to achieve this specify a <i>target selector</i> on the advanced tab.

#### EDI mapping
The EDI mapping file specifying the format of the request messages.

<i>Required</i>

#### Delete files
Specify whether to delete the source file after a (successful) transformation.

When set to <i>true</i>, it will only have an effect if the inbound message has a <code>File</code> payload or a <code>file_originalFile</code> header value containing either a <code>File</code> instance or a <code>String</code> representing the original file path. 

Default is <i>false</i>.

#### Validate
Whether to perform data validation when processing the EDI content.

Note this validation only applies to the <b>contents</b> of fields/components/subcomponents that have one or more of the following settings specified: <i>data type</i>, <i>min length</i> or <i>max length</i>. The <b>structure</b> of the message is always validated during processing, irregardless of this setting.

Default is <i>false</i>.

#### Ignore new lines
Whether to ignore "unexpected" new lines in the EDI content (i.e. new lines not immediately following the end of a segment).

Default is <i>false</i>.

#### Charset
Character set to be used to decode the bytes of the incoming message into (readable) text. If the payload of the incoming message is already in "text form" (i.e. a <code>String</code>, <code>Reader</code> or <code>StreamSource</code>), this property is not used. 

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)

#### Target selector
Smooks selector expression for splitting the EDI message stream into fragments for the output XML messages.

Default is <code>$document</code>, which results in the entire incoming EDI message stream being transformed into a single XML message.

#### Selector namespace
Optional XML namespace for the selector expression.

If specified, XML elements will only match the <i>target selector</i> expression if they have the exact same namespace. If not specified (the default), the namespace is ignored when matching XML elements to the <i>target selector</i> expression.

#### Requires reply
Whether this transformer must send at least one message to the output channel for each incoming message. If enabled and an incoming message doesn't result in at least one outgoing message, a <code>ReplyRequiredException</code> is thrown instead. 

Default is <i>true</i>.

#### Apply sequence
Whether to add the sequence headers (<code>correlationId</code>, <code>sequenceNumber</code> and <code>sequenceSize</code>) to the output messages.

Note that because of the streaming nature of this transformer, the correct value for the <code>sequenceSize</code> header cannot be determined when sending the output messages: value <code>-1</code> is used instead.

Default is <i>false</i>.

#### Send timeout
Set the timeout (in milliseconds) for sending messages to the output channel. 

Default is <code>-1</code>, i.e. wait indefinitely.

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

