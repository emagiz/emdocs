# Byte array length header (de)serializer
#### Serializes data preceded by a binary header indicating the data length
Reads data in an <code>InputStream</code> to a <code>byte[]</code>; data must be preceded by a binary length (network byte order, not included in resulting <code>byte[]</code>).

Writes a <code>byte[]</code> to an <code>OutputStream</code> after a binary length.

The length field contains the length of data following the length field (network byte order). The default length field is a 4 byte signed integer. During deserialization, negative values will be rejected. Other options are an unsigned byte, and unsigned short.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Header size
Specifies the header size.

Valid header sizes are:
- <code>4</code> : Default length-header field, allows for data up to 2**31-1 bytes.
- <code>2</code> : An unsigned short, for data up to 2**16 bytes.
- <code>1</code> : A single unsigned byte, for data up to 255 bytes.

Default is <code>4</code>.

#### Max message size
The maximum supported message size (in bytes) for this (de)serializer.

Default is <i>2048</i> (2 KiB).

To avoid memory exhaustion due to a badly behaved client (one that does not adhere to the protocol of the configured serializer), this (de)serializer imposes a maximum message size. If the size is exceeded by an incoming message, an exception will be thrown. The default maximum message size is 2048 bytes, and can be increased by setting the <i>maxMessageSize</i> property.

