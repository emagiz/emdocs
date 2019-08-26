---
id: custom-field
title: Custom field
sidebar_label: Custom field
---
#### Field number
Field number (in the range 2 - 127) of the fields that should be encoded/decoded using these custom field settings.


<code>CustomField</code> implementation that encodes/decodes text values that are composed of multiple sub-values, each separated by a delimiter.

#### Delimiter
Delimiter that separates the sub-values, e.g. <code>;</code>.

#### End with delimiter
If <code>true</code>, the encoded value will always end with a delimiter; if <code>false</code> the last sub-value is not followed by a delimiter (if the encoded value in this case ends with a delimiter, this indicates the last sub-value is the empty string).


<code>CustomField</code> implementation that encodes/decodes numeric values that are composed of multiple sub-values, each with a pre-defined fixed length.

#### Lengths
Comma separated list of the fixed lengths of each sub-value (from left to right), e.g. <code>4,12,8</code>.


<code>CustomField</code> implementation that encodes/decodes text values that are composed of multiple sub-values, each with a pre-defined fixed length.

#### Lengths
Comma separated list of the fixed lengths of each sub-value (from left to right), e.g. <code>4,12,8</code>.


<code>CustomField</code> implementation that encodes/decodes <code>DateTime</code> values using a configurable format pattern.

#### Pattern
Pattern string for parsing/printing DateTime values, e.g. <code>yyyyMMddHHmmss</code>.


<code>CustomField</code> implementation that decodes fields containing a (nested) <code>IsoMessage</code>. 

Internally, a <code>BytesToXmlTransformer</code> is used to parse the ISO8583 bytes into an <code>IsoMessage</code> object and to serialize these objects to XML. Because the nested message may not contain a message type and messages without a type cannot be parsed, this decoder can add one to the nested message: such a modified message will always be of type <code>0x9999</code>. The message factory of the provided transformer therefore needs to be configured for the expected message type(s), or for type <code>0x9999</code> if the messages don't contain a message type. 

This decoder can also shift the bits of the primary bitmap of the nested message, which is useful in situations where this bitmap is not quite a standard ISO8583 bitmap as used for "normal", non-nested messages. For example, when the first bit of the primary bitmap of the nested message is used for the first field instead of indicating the presence of a secondary bitmap, you can still parse the message if you shift the bitmap 1 bit to the right. 

Note that this strictly is a decoder, intended to be used when parsing ISO8583 messages. This class is not an encoder that can be used to create new ISO8583 messages.

#### Use binary messages
Sets whether to create and parse messages in binary or in ASCII format. 

Default is <code>false</code> (create and parse ASCII messages).

#### Parse maps
Registers the parse maps to be used when parsing messages. 

By default no parse maps are registered, but they are required for parsing messages.

#### Custom fields
Registers custom field encoder/decoders that are used for parsing and creating messages. 

By default no custom field encoders/decoders are registered.

#### Misses type header
If true, incoming messages are expected to not contain the type header. Since this header is required for parsing ISO8583 messages, this decoder will add the message type <code>0x9999</code> to all messages. If <code>false</code>, it is expected the message already contains the correct type header. 

Default is <code>false</code>, indicating that incoming messages do contain the type header.

#### Shift bitmap
Shifts the primary bitmap in the message the specified number of bits to the right. Use <code>0</code> for no shifting, or a negative value for shifting to the left. 

Default is <code>0</code>, which disables any bitmap shifting. 

<b>Note:</b>
The shifting method of this class only works on messages with an <u>8 byte binary bitmap</u>.

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


<code>CustomField</code> implementation that encodes fields containing a (nested) <code>IsoMessage</code>. 

Internally, an <code>XmlToBytesTransformer</code> is used to deserialize XML into an <code>IsoMessage</code> object and to encode these objects to ISO8583. Because the outgoing message may be required to not contain a message type, this encoder can remove the type header from the nested message.

This encoder can also shift the bits of the primary bitmap of the nested message, which is useful in situations where this bitmap is required to be not quite a standard ISO8583 bitmap as used for "normal", non-nested messages. For example, when the first bit of the primary bitmap of the nested message is used for the first field instead of indicating the presence of a secondary bitmap, you can create the correct outgoing message if you shift the bitmap 1 bit to the left.

Note that this strictly is an encoder, intended to be used when creating ISO8583 messages. This class is not a decoder that can be used to parse ISO8583 messages.

#### Use binary messages
Sets whether to create and parse messages in binary or in ASCII format. 

Default is <code>false</code> (create and parse ASCII messages).

#### Custom fields
Registers custom field encoder/decoders that are used for parsing and creating messages. 

By default no custom field encoders/decoders are registered.

#### Remove type header
If <code>true</code>, outgoing messages are expected to not contain the type header. Since this header is normally always present in ISO8583 messages, this encoder will remove the header from all messages. If <code>false</code>, the type header is not removed. 

Default is <code>false</code>, indicating that outgoing messages should contain the type header.

#### Shift bitmap
Shifts the primary bitmap in the outgoing message the specified number of bits to the right. Use <code>0</code> for no shifting, or a negative value for shifting to the left. 

Default is <code>0</code>, which disables any bitmap shifting. 

<b>Note:</b>
The shifting method of this class only works on messages with an <u>8 byte binary bitmap</u>.

#### Convert bitmaps
In situations where outgoing messages use the ASCII format but the bitmaps should be using the binary format (which is unusual and not supported by <i>j8583</i>, but allowed by ISO8583), the bitmaps (primary and optionally secondary) need to be converted to binary. In these cases you should set this property to <code>true</code> and make sure the message factory uses ASCII messages.

Default is <code>false</code>, which doesn't convert the bitmaps.

#### Assign date
Sets whether the current date should be set in field 7 on newly created messages. 

Default is <code>false</code>.

#### Character encoding
Sets the character encoding used for parsing and encoding ALPHA, LLVAR and LLLVAR fields. 

Default is the value of the <code>file.encoding</code> system property.

#### EXT
Sets the ETX character to be sent at the end of the message. 

Default is <code>-1</code>, which indicates nothing should be sent as terminator.

#### Force secondary bitmap
Sets whether to include a secondary bitmap when creating messages even if it's not needed. 

Default is <code>false</code>.

#### Trace number generator type
<code>TraceNumberGenerator</code> used to generate trace numbers that should be set in field 11 on newly created messages. 

Default is <code>empty</code>, indicating no trace numbers should be set in field 11 on newly created messages.

#### ISO headers
Sets the ISO headers to be used when creating messages. 

By default, no ISO headers are used when creating messages of any type.


<code>CustomField</code> implementation that encodes/decodes Triple DES encrypted + Base64 encoded values.

#### Key
Triple DES key for encrypting/decrypting values, e.g. <code>194837294857593owc2394ow</code>.


<code>CustomField</code> implementation that decodes String values (possibly containing 'unsafe' bytes) as Base64 String values, and encodes Base64 String values as String values (possibly containing 'unsafe' bytes). 

By using this encoder, it's possible to use <code>ALPHA</code>, <code>LLVAR</code> or <code>LLLVAR</code> fields to store binary data. Please note that this is <b>not recommended</b>: if possible, use a <code>BINARY</code>, <code>LLBIN</code> or <code>LLLBIN</code> field instead.

#### Auto-detect Base64
If <i>true</i>, the input during encoding is scanned to see if it's a Base64 string or not. If it is, it will be decoded and the resulting bytes will be converted to the output string. If not, the input is returned unaltered.

If <i>false</i>, when the input is not a Base64 string an exception will be thrown. 

Default is <i>false</i>.

#### Charset
Sets the character set used for encoding/decoding a <code>byte[]</code> as a String. You probably want to use the exact same character set the <i>MessageFactory</i> is using. 

Default is the value of the <code>file.encoding</code> system property.


Simple implementation of a <code>TraceNumberGenerator</code> with an internal number that is increased in memory but is not stored anywhere.

#### Initial trace number
The value for the first generated trace number; a number between 1 and 999999.

<i>Required</i>

