
Payload transformer that encodes MIME messages to S/MIME messages.
Transformer that encodes MIME messages to S/MIME messages.

For most uses cases, this needs to be combined with an XML to MIME message transformer.


Sign message
Whether or not the message should be signed.

Default is <code>True</code>.



Encrypt message
Whether or not the message should be encoded.

While in theory it is possible to sign and encrypt a message in any order and even multiple times, this is not recommended in reality because even the common mail clients do not support such use of S/MIME very well.
Therefore, the following options are available:
- Signing only
- Encrypting only
- First signing, then encrypting

Default is <code>True</code>.



Key store URL
Location of the store used to obtain the private S/MIME (JKS) key with which to sign the message.

<i>Required</i>, if signing message.



Key store password
The password with which to unlock the key store.

<i>Required</i>, if signing message.



Private key password
The password used to access the private key inside the key store.

<i>Required</i>, if signing message.



Trust store URL
Location of the store used to obtain the S/MIME (JKS) key with which to encrypt the message.

<i>Required</i>, if encrypting message.


Trust store password
The password used to access the trust store.

<i>Required</i>, if encrypting message.



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

