# Error to XML transformer
#### Transformer that converts error messages into XML messages.
Transformer that converts error messages (i.e. a message with a <code>Throwable</code> payload) to XML.

The result of this transformation will be a complete, well-formed XML document as a string (the default), XOM document or DOM document. The layout of this document is defined by the XML schema located at:
<code>classpath:com/emagiz/components/error/emagiz-error-1.0.xsd</code>

The payload of the failed message is converted to a string value using an <i>XML to string transformer</i> or <i>Base64 encoding transformer</i> (depending on the type), or if that fails by calling <code>String.valueOf(Object)</code> on the payload. This potentially expensive conversion can be skipped by setting <i>omit payload</i>. To further reduce the size of the resulting XML, the stacktrace can also be omitted using <i>omit stack trace</i>.

#### Omit stack trace
Whether to omit the stack trace of the exception (if there is one) in the resulting XML or not. 

Default is <i>true</i>.



#### Omit payload
Whether to omit the payload of the original message (if there is one) in the resulting XML or not. 

Default is <i>false</i>.

#### Restore headers
Determines how to attempt restoring the messages headers from the original message on the resulting error message. This includes restoring the message history and tracking information (if any) of the original message.

If the exception message doesn't contain the original message, headers cannot be restored, but setting this property to a value other than <i>do not restore headers</i> will not cause exceptions in such a case.

Options for restoring the message headers of the input message and the original message on the output message are:
- <b>Restore all headers</b>: Restore all input and original headers on the output message. In case of duplicate header names, the input header takes precedence over the original header.
- <b>Restore all headers (with overwrite)</b>: Restore all input and original headers on the output message. In case of duplicate header names, the original header overwrites the input header.
- <b>Restore serializable headers only</b>: Only restore serializable input and original headers on the output message. In case of duplicate header names, the input header takes precedence over the original header.
- <b>Restore serializable headers only (with overwrite)</b>: Only restore serializable input and original headers on the output message. In case of duplicate header names, the original header overwrites the input header.
- <b>Do not restore headers</b>: No original headers are restored on the output message, but all input headers are (this includes any non-serializable values).

Note that the <i>history</i> header is treated slightly different from what is described above: multiple values of this header are always merged to preserve the correct message history (unless option <i>do not restore headers</i> is used).

Please be aware that the <i>replyChannel</i> and <i>errorChannel</i> headers that are used for the error handling of inbound gateways are non-serializable: if you want to "loop back" the error channel of an inbound gateway to its reply channel, you must select either <i>restore all headers</i> or <i>do not restore headers</i> in order for the error handling to work properly.

Default is <i>restore serializable headers only</i>.

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Result type
Sets the result type (<code>XomDocument</code>, <code>DomDocument</code> or <code>String</code>) for the transformation. 

Default is <code>String</code>.


#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

