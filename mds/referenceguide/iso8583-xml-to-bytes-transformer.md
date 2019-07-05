---
id: iso8583-xml-to-bytes-transformer
title: ISO8583 XML to bytes transformer
sidebar_label: ISO8583 XML to bytes transformer
---
#### Transformer that converts XML messages to ISO8583 byte messages.
Transformer that converts XML messages to ISO8583 byte messages, using a <code>MessageFactory</code> of the <i>j8583</i> project. 

The payload of the incoming message must be a <code>&lt;iso8583:message&gt;</code>, as defined by the XML schema located at:
<code>classpath:com/emagiz/components/iso8583/emagiz-iso8583-1.0.xsd</code>

A note on the use of fields with a <code>CustomField</code>:
Because this transformer parses XML documents into the field values of an <code>IsoMessage</code> and needs to know how to deserialize these values from XML, the use of custom fields is only supported in one of the following two cases:
&bull; the custom field value is of the exact same object class as the default <i>j8583</i> parser uses (e.g. <code>String</code> for fields of type ALPHA, <code>byte[]</code> for fields of type BINARY, etc) --> this way the custom values can be parsed from XML the same way as "normal" values would (but this makes its use quite limited) 
&bull; the custom field is of type ALPHA, LLVAR, LLLVAR, BINARY, LLBIN or LLLBIN and the custom field is an instance of <code>AbstractCustomField</code> --> this way the custom values can be converted to XML by calling its <code>parseXml</code> method

Note that the type restriction in the second case is hardly a limiting factor in practice, as the <i>j8583</i> library (version 1.5.1) seems to ignore custom fields for the other types anyway (except for NUMERIC in a non-binary message).

#### Use binary messages
Sets whether to create and parse messages in binary or in ASCII format. 

Default is <code>false</code> (create and parse ASCII messages).

#### Custom fields
Registers custom field encoder/decoders that are used for parsing and creating messages. 

By default no custom field encoders/decoders are registered.

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


Simple implementation of a <code>TraceNumberGenerator</code> with an internal number that is increased in memory but is not stored anywhere.

#### Initial trace number
The value for the first generated trace number; a number between 1 and 999999.

<i>Required</i>

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

