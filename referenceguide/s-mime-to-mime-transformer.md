
Payload transformer that decodes S/MIME messages to MIME messages.
Transformer that decodes S/MIME messages to MIME messages.

For most uses cases, this needs to be combined with a MIME message to XML transformer.


Key store URL
Location of the key store used to obtain the Private S/MIME (JKS) key to decrypt the encrypted message with.

<i>Required</i>



Key store password
The password with which to unlock the key store.

<i>Required</i>



Private key password
The password used to access the private key inside the key store.

<i>Required</i>



 Fail on non-S/MIME content
Set whether or not the flow should continue if the received content is not S/MIME to start with. If set to True, such message will be passed on to the output channel, without any changes. If set to False, an exception will be thrown.

Default is <code>False</code>.



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

