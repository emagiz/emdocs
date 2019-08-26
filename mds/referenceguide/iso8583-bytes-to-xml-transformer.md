---
id: iso8583-bytes-to-xml-transformer
title: ISO8583 bytes to XML transformer
sidebar_label: ISO8583 bytes to XML transformer
---
#### Transformer that converts ISO8583 byte messages to XML.
Transformer that converts ISO8583 byte messages to XML, using a MessageFactory of the <i>j8583</i> project. 

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is defined by the XML schema located at:
<code>classpath:com/emagiz/components/iso8583/emagiz-iso8583-1.0.xsd</code>

A note on the use of fields with a <code>CustomField</code>:
Because this transformer builds XML documents from the field values of an IsoMessage and needs to know how to serialize these values to XML, the use of custom fields is only supported in one of the following two cases: 
&bull; the custom field value is of the exact same object class as the default <i>j8583</i> parser uses (e.g. <code>String</code> for fields of type ALPHA, <code>byte[]</code> for fields of type BINARY, etc) --> this way the custom values can be converted to XML the same way as "normal" values would (but this makes its use quite limited)
&bull; the custom field is of type ALPHA, LLVAR, LLLVAR, BINARY, LLBIN or LLLBIN and the value object is an instance of <code>CustomFieldValue</code> --> this way the custom values can be converted to XML by calling its <code>addToXml</code> method

Note that the type restriction in the second case is hardly a limiting factor in practice, as the <i>j8583</i> library (version 1.5.1) seems to ignore custom fields for the other types anyway (except for NUMERIC in a non-binary message).

#### Use binary messages
Sets whether to create and parse messages in binary or in ASCII format. 

Default is <code>false</code> (create and parse ASCII messages).

#### Parse maps
Registers the parse maps to be used when parsing messages. 

By default no parse maps are registered, but they are required for parsing messages.

#### Custom fields
Registers custom field encoder/decoders that are used for parsing and creating messages. 

By default no custom field encoders/decoders are registered.

#### Result type
Specifies the result type of the XML payload.

Default: <code>String</code>

#### ISO header length
Sets the expected length of the ISO header for the messages this transformer will receive, after which the message type and the rest of the message must come. 

Default is <code>0</code>, which indicates no header (first field of the message is expected to specify the message type).

#### Allow empty messages
If <code>true</code>, ISO8583 messages that don't contain any fields after parsing will not cause an exception but will generate an empty <code>&lt;iso8583:message type="..."/&gt;</code> XML message. 

A message can be empty for one of the following reasons: 
1 - the message couldn't correctly be parsed because it contained a field that wasn't specified in the parse map (this points to a real problem, as there apparently is a mismatch between the message definition and the actual messages)
2 - the message didn't contain any of the fields specified in the parse map (fields are always optional, so this technically is correct)
3 - the parse map for the message type is empty and the message too (which also is technically correct)

Default is <code>false</code>, which causes a (runtime) exception to be thrown when parsing results in an empty message. In most cases this is the "correct" behaviour, as empty messages are most likely caused by reason #1 (see above).

#### Convert bitmaps
In situations where incoming messages use the ASCII format but the bitmaps are using the binary format (which is unusual and not supported by <i>j8583</i>, but allowed by ISO8583), the bitmaps (primary and optionally secondary) need to be converted to ASCII before the <code>MessageFactory</code> can parse it. In these cases you should set this property to <code>true</code> and make sure the message factory uses ASCII messages. 

Default is <code>false</code>, which doesn't convert the bitmaps.

#### Character encoding
Sets the character encoding used for parsing and encoding ALPHA, LLVAR and LLLVAR fields. 

Default is the value of the <code>file.encoding</code> system property.

#### Ignore last missing field
Setting this property to true avoids getting a ParseException when parsing messages that don't have the last field specified in the bitmap. This is common with certain providers where field 128 is specified in the bitmap but not actually included in the messages. 

Default is <code>false</code>.

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
id: iso8583-bytes-to-xml-transformer
title: ISO8583 bytes to XML transformer
sidebar_label: ISO8583 bytes to XML transformer
---
#### Transformer that converts ISO8583 byte messages to XML.
Transformer that converts ISO8583 byte messages to XML, using a MessageFactory of the <i>j8583</i> project. 

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is defined by the XML schema located at:
<code>classpath:com/emagiz/components/iso8583/emagiz-iso8583-1.0.xsd</code>

A note on the use of fields with a <code>CustomField</code>:
Because this transformer builds XML documents from the field values of an IsoMessage and needs to know how to serialize these values to XML, the use of custom fields is only supported in one of the following two cases: 
&bull; the custom field value is of the exact same object class as the default <i>j8583</i> parser uses (e.g. <code>String</code> for fields of type ALPHA, <code>byte[]</code> for fields of type BINARY, etc) --> this way the custom values can be converted to XML the same way as "normal" values would (but this makes its use quite limited)
&bull; the custom field is of type ALPHA, LLVAR, LLLVAR, BINARY, LLBIN or LLLBIN and the value object is an instance of <code>CustomFieldValue</code> --> this way the custom values can be converted to XML by calling its <code>addToXml</code> method

Note that the type restriction in the second case is hardly a limiting factor in practice, as the <i>j8583</i> library (version 1.5.1) seems to ignore custom fields for the other types anyway (except for NUMERIC in a non-binary message).

#### Use binary messages
Sets whether to create and parse messages in binary or in ASCII format. 

Default is <code>false</code> (create and parse ASCII messages).

#### Parse maps
Registers the parse maps to be used when parsing messages. 

By default no parse maps are registered, but they are required for parsing messages.

#### Custom fields
Registers custom field encoder/decoders that are used for parsing and creating messages. 

By default no custom field encoders/decoders are registered.

#### Result type
Specifies the result type of the XML payload.

Default: <code>String</code>

#### ISO header length
Sets the expected length of the ISO header for the messages this transformer will receive, after which the message type and the rest of the message must come. 

Default is <code>0</code>, which indicates no header (first field of the message is expected to specify the message type).

#### Allow empty messages
If <code>true</code>, ISO8583 messages that don't contain any fields after parsing will not cause an exception but will generate an empty <code>&lt;iso8583:message type="..."/&gt;</code> XML message. 

A message can be empty for one of the following reasons: 
1 - the message couldn't correctly be parsed because it contained a field that wasn't specified in the parse map (this points to a real problem, as there apparently is a mismatch between the message definition and the actual messages)
2 - the message didn't contain any of the fields specified in the parse map (fields are always optional, so this technically is correct)
3 - the parse map for the message type is empty and the message too (which also is technically correct)

Default is <code>false</code>, which causes a (runtime) exception to be thrown when parsing results in an empty message. In most cases this is the "correct" behaviour, as empty messages are most likely caused by reason #1 (see above).

#### Convert bitmaps
In situations where incoming messages use the ASCII format but the bitmaps are using the binary format (which is unusual and not supported by <i>j8583</i>, but allowed by ISO8583), the bitmaps (primary and optionally secondary) need to be converted to ASCII before the <code>MessageFactory</code> can parse it. In these cases you should set this property to <code>true</code> and make sure the message factory uses ASCII messages. 

Default is <code>false</code>, which doesn't convert the bitmaps.

#### Character encoding
Sets the character encoding used for parsing and encoding ALPHA, LLVAR and LLLVAR fields. 

Default is the value of the <code>file.encoding</code> system property.

#### Ignore last missing field
Setting this property to true avoids getting a ParseException when parsing messages that don't have the last field specified in the bitmap. This is common with certain providers where field 128 is specified in the bitmap but not actually included in the messages. 

Default is <code>false</code>.

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

