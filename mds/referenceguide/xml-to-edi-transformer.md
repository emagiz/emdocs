---
id: xml-to-edi-transformer
title: XML to EDI transformer
sidebar_label: XML to EDI transformer
---
#### Transforms XML messages into EDI (text) messages
Transformer that uses <i>Smooks</i> for converting XML documents into EDI messages.

The input messages must have the exact same XML format as the output messages of the <i>EDI to XML transformer</i>.

Supports the following message payload types for the XML content:
- <code>String</code>
- <code>byte[]</code>
- <code>File</code>
- <code>InputStream</code>
- <code>Reader</code>
- <code>StreamSource</code>

The resulting EDI messages will always be returned as a <code>String</code> value.

#### EDI mapping
The EDI mapping file specifying the format of the request messages.

<i>Required</i>

#### Validate
Whether to perform data validation when processing the EDI content.

Note this validation only applies to the <b>contents</b> of fields/components/subcomponents that have one or more of the following settings specified: <i>data type</i>, <i>min length</i> or <i>max length</i>. The <b>structure</b> of the message is always validated during processing, irregardless of this setting.

Default is <i>false</i>.

#### Segment line break
Optional newline character(s) that will be used as line breaks between segments. If the segment delimiter already ends with such a line break, this setting has no effect. 

Default is <i>empty</i>, meaning no line breaks between segments will be added.


The following options for the newline character(s) are available:

<b>Carriage return</b>, the newline character sequence on:
 - Commodore 8-bit machines
 - Acorn BBC
 - ZX Spectrum
 - TRS-80
 - Apple II family
 - Mac OS up to version 9
 - OS-9

<b>Carriage return + line feed</b>, the newline character sequence on:
 - Microsoft Windows
 - DEC TOPS-10
 - RT-11 and most other early non-Unix and non-IBM OSes
 - CP/M
 - MP/M
 - DOS (MS-DOS, PC DOS, etc.)
 - Atari TOS
 - OS/2 
 - Symbian OS
 - Palm OS
 - Amstrad CPC

<b>Line feed</b>, the newline character sequence on:
 - Multics
 - Unix and Unix-like systems (GNU/Linux, OS X, FreeBSD, AIX, Xenix, etc.)
 - BeOS
 - Amiga
 - RISC OS

<b>Line feed + carriage return</b>, the newline character sequence on:
 - Acorn BBC
 - RISC OS spooled text output

#### Charset
Character set to be used to decode the bytes of the <b>incoming XML message</b> into (readable) text. If the payload of the incoming message is already in "text form" (i.e. a <code>String</code>, <code>Reader</code> or <code>StreamSource</code>), this property is not used. 

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)

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
id: xml-to-edi-transformer
title: XML to EDI transformer
sidebar_label: XML to EDI transformer
---
#### Transforms XML messages into EDI (text) messages
Transformer that uses <i>Smooks</i> for converting XML documents into EDI messages.

The input messages must have the exact same XML format as the output messages of the <i>EDI to XML transformer</i>.

Supports the following message payload types for the XML content:
- <code>String</code>
- <code>byte[]</code>
- <code>File</code>
- <code>InputStream</code>
- <code>Reader</code>
- <code>StreamSource</code>

The resulting EDI messages will always be returned as a <code>String</code> value.

#### EDI mapping
The EDI mapping file specifying the format of the request messages.

<i>Required</i>

#### Validate
Whether to perform data validation when processing the EDI content.

Note this validation only applies to the <b>contents</b> of fields/components/subcomponents that have one or more of the following settings specified: <i>data type</i>, <i>min length</i> or <i>max length</i>. The <b>structure</b> of the message is always validated during processing, irregardless of this setting.

Default is <i>false</i>.

#### Segment line break
Optional newline character(s) that will be used as line breaks between segments. If the segment delimiter already ends with such a line break, this setting has no effect. 

Default is <i>empty</i>, meaning no line breaks between segments will be added.


The following options for the newline character(s) are available:

<b>Carriage return</b>, the newline character sequence on:
 - Commodore 8-bit machines
 - Acorn BBC
 - ZX Spectrum
 - TRS-80
 - Apple II family
 - Mac OS up to version 9
 - OS-9

<b>Carriage return + line feed</b>, the newline character sequence on:
 - Microsoft Windows
 - DEC TOPS-10
 - RT-11 and most other early non-Unix and non-IBM OSes
 - CP/M
 - MP/M
 - DOS (MS-DOS, PC DOS, etc.)
 - Atari TOS
 - OS/2 
 - Symbian OS
 - Palm OS
 - Amstrad CPC

<b>Line feed</b>, the newline character sequence on:
 - Multics
 - Unix and Unix-like systems (GNU/Linux, OS X, FreeBSD, AIX, Xenix, etc.)
 - BeOS
 - Amiga
 - RISC OS

<b>Line feed + carriage return</b>, the newline character sequence on:
 - Acorn BBC
 - RISC OS spooled text output

#### Charset
Character set to be used to decode the bytes of the <b>incoming XML message</b> into (readable) text. If the payload of the incoming message is already in "text form" (i.e. a <code>String</code>, <code>Reader</code> or <code>StreamSource</code>), this property is not used. 

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)

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

