---
id: xml-to-flat-file-transformer
title: XML to flat file transformer
sidebar_label: XML to flat file transformer
---
#### Transformer that converts XML documents to flat-file format
Transformer that converts XML documents to flat-file format. 

This transformer uses a Spring Batch FlatFileItemWriter to format and write the flat file data. 

#### Number of columns
Number of columns that this XML to flat file transformer has.

#### Charset
Character set to be used for writing the output data.

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)

#### Delimiter
The delimiter character.

Any unicode string literals of the form <code>\uXXXX</code> (where <code>XXXX</code> is the hexadecimal code of the unicode character) are replaced by the actual unicode character. The tab character, for example, is <code>\u0009</code>.

Default is a comma.

#### Use string result
Normally the result of this transformer will be a byte array. By setting this property to <i>true</i>, the result will be a string instead.

Note that using byte arrays has (slightly) better performance and that the <i>charset</i> setting is irrelevant when using a string result.

Default is <i>false</i>.

#### Line separator
Character(s) used for separating the lines.

Any unicode string literals of the form <code>\uXXXX</code> (where <code>XXXX</code> is the hexadecimal code of the unicode character) are replaced by the actual unicode character. A "Linux enter", for example, is <code>\u000A</code> and a "Windows enter" is <code>\u000D\u000A</code>.

Defaults to the system property <i>line.separator</i>.

#### Minimum length
Minimum length for the formatted string. If the result of the formatting is shorter than the minimum, a runtime exception is thrown.

Default is '0', which indicates no minimum length.

#### Maximum length
Maximum length for the formatted string. If the result of the formatting is longer than the maximum, a runtime exception is thrown.

Default is '0', which indicates no maximum length.


Namespace prefix of the XML nodes in the XPath expression

<i>Optional, but required when namespace URI is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>


Namespace URI of the XML nodes in the XPath expression.

<i>Optional, but required when namespace prefix is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>


XPath expression that returns a value (boolean or string) used for filtering the message. In case of a boolean value, <code>true</code> accepts the message and <code>false</code> discards it. In case of a string value, this decision depends on the value of the <i>match value</i> and <i>match type</i> settings.

<i>Required</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>

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
id: xml-to-flat-file-transformer
title: XML to flat file transformer
sidebar_label: XML to flat file transformer
---
#### Transformer that converts XML documents to flat-file format
Transformer that converts XML documents to flat-file format. 

This transformer uses a Spring Batch FlatFileItemWriter to format and write the flat file data. 

#### Number of columns
Number of columns that this XML to flat file transformer has.

#### Charset
Character set to be used for writing the output data.

Default is <code>UTF-8</code>.

The supported encodings vary between different implementations of the Java platform, however the following encodings should always be available on any implementation: <b><i>US-ASCII</i></b>, <b><i>ISO-8859-1</i></b>, <b><i>UTF-8</i></b>, <b><i>UTF-16BE</i></b>, <b><i>UTF-16LE</i></b>, <b><i>UTF-16</i></b>.

A list of the supported encodings in the Sun/Oracle Java 6 SE runtime environment can be found <a href="http://docs.oracle.com/javase/6/docs/technotes/guides/intl/encoding.doc.html">here</a>.

Additionally, eMagiz contains build-in support for the following two encodings:
 - <b><i>x-UTF-8-BOM</i></b> (eight-bit Unicode Transformation Format, with byte-order mark)
 - <b><i>x-UTF-16BE-BOM</i></b> (sixteen-bit UTF, big-endian byte order, with byte-order mark)

#### Delimiter
The delimiter character.

Any unicode string literals of the form <code>\uXXXX</code> (where <code>XXXX</code> is the hexadecimal code of the unicode character) are replaced by the actual unicode character. The tab character, for example, is <code>\u0009</code>.

Default is a comma.

#### Use string result
Normally the result of this transformer will be a byte array. By setting this property to <i>true</i>, the result will be a string instead.

Note that using byte arrays has (slightly) better performance and that the <i>charset</i> setting is irrelevant when using a string result.

Default is <i>false</i>.

#### Line separator
Character(s) used for separating the lines.

Any unicode string literals of the form <code>\uXXXX</code> (where <code>XXXX</code> is the hexadecimal code of the unicode character) are replaced by the actual unicode character. A "Linux enter", for example, is <code>\u000A</code> and a "Windows enter" is <code>\u000D\u000A</code>.

Defaults to the system property <i>line.separator</i>.

#### Minimum length
Minimum length for the formatted string. If the result of the formatting is shorter than the minimum, a runtime exception is thrown.

Default is '0', which indicates no minimum length.

#### Maximum length
Maximum length for the formatted string. If the result of the formatting is longer than the maximum, a runtime exception is thrown.

Default is '0', which indicates no maximum length.


Namespace prefix of the XML nodes in the XPath expression

<i>Optional, but required when namespace URI is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>


XPath expression that returns a value (boolean or string) used for filtering the message. In case of a boolean value, <code>true</code> accepts the message and <code>false</code> discards it. In case of a string value, this decision depends on the value of the <i>match value</i> and <i>match type</i> settings.

<i>Required</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>


Namespace URI of the XML nodes in the XPath expression.

<i>Optional, but required when namespace prefix is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>

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

