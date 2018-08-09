# File to string transformer
#### Transforms file messages to string messages
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/files.html#file-transforming" target="_blank">Documentation</a>


#### Charset
Character set to be used for reading the file contents into a string.

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)

#### Delete files
Specify whether to delete source files after transforming them.

This will only take effect if the Message payload is the actual source File instance
 or if the original File instance (or its path) is available in the header.

Default: <i> false </i>

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

