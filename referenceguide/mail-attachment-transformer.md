# Mail attachment transformer
#### Payload transformer that transforms messages into mail attachment messages.
Transformer that converts the message payload to a byte array and sets the MailHeaders.ATTACHMENT_FILENAME message header, resulting in a message that will be mapped to an e-mail attachment by downstream mail outbound channel adapters. 

Supported payload types are byte[] and all types supported by <i>Xml To String Transformer</i> (i.e. String, DOM Document, XOM Document and Source).


#### Filename format
Format, as used by FormatFileNameGenerator, that will be used for generating the value for the MailHeaders.ATTACHMENT_FILENAME header. 

Note that you can also use literal values: the format 'example.txt' will result in all mail attachments being named 'example.txt'. 

Default is '*FILE_NAME**FILE_EXT*'.

#### Overwrite header
Whether an existing MailHeaders.ATTACHMENT_FILENAME message header value of the incoming message should be overwritten by this transformer or not. 

#### Charset
Charset that is used when transforming the message payload from a String or XML to a byte array. If the payload is already a byte[], this property is not used. 

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

