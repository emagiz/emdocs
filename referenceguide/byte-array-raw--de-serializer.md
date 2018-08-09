# Byte array raw (de)serializer
#### Serializes data without doing anything with the payload
A byte array (de)serializer that does nothing with the payload; sends it raw. Message termination for assembly purposes is signaled by the client closing the connection. The serializer does not, itself, close the connection after writing the bytes.

Because the socket must be closed to indicate message end, this (de)serializer can only be used by uni-directional (non-collaborating) channel adapters, and not by gateways.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Treat timeout as end of message
Set to <code>true</code> to treat socket timeouts as a normal EOF and emit the (possibly partial) message. If <code>false</code>, a <code>SocketTimeoutException</code> is thrown instead.

Default is <code>false</code>.

#### Max message size
The maximum supported message size (in bytes) for this (de)serializer.

Default is <i>2048</i> (2 KiB).

To avoid memory exhaustion due to a badly behaved client (one that does not adhere to the protocol of the configured serializer), this (de)serializer imposes a maximum message size. If the size is exceeded by an incoming message, an exception will be thrown. The default maximum message size is 2048 bytes, and can be increased by setting the <i>maxMessageSize</i> property.

