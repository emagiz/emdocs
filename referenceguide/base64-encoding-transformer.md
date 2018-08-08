
Charset
Character set that is used when Base64-encoding string payloads. If the payload is a byte array, this property is not used.

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)


Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>


Id
Name that uniquely identifies this flow component.

<i>Required</i>


Input channel
Channel to consume the input messages from.

<i>Required</i>

