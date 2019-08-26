---
id: byte-array-stx-etx--de-serializer
title: Byte array STX/ETX (de)serializer
sidebar_label: Byte array STX/ETX (de)serializer
---
#### Serializes data prefixed with STX and terminated by ETX
Reads data in an <code>InputStream</code> to a <code>byte[]</code>; data must be prefixed by <i>&lt;stx&gt;</i> and terminated by <i>&lt;etx&gt;</i> (not included in resulting <code>byte[]</code>).

Writes a <code>byte[]</code> to an <code>OutputStream</code> prefixed by <i>&lt;stx&gt;</i> terminated by <i>&lt;etx&gt;</i>.

#### Max message size
The maximum supported message size (in bytes) for this (de)serializer.

Default is <i>2048</i> (2 KiB).

To avoid memory exhaustion due to a badly behaved client (one that does not adhere to the protocol of the configured serializer), this (de)serializer imposes a maximum message size. If the size is exceeded by an incoming message, an exception will be thrown. The default maximum message size is 2048 bytes, and can be increased by setting the <i>maxMessageSize</i> property.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: byte-array-stx-etx--de-serializer
title: Byte array STX/ETX (de)serializer
sidebar_label: Byte array STX/ETX (de)serializer
---
#### Serializes data prefixed with STX and terminated by ETX
Reads data in an <code>InputStream</code> to a <code>byte[]</code>; data must be prefixed by <i>&lt;stx&gt;</i> and terminated by <i>&lt;etx&gt;</i> (not included in resulting <code>byte[]</code>).

Writes a <code>byte[]</code> to an <code>OutputStream</code> prefixed by <i>&lt;stx&gt;</i> terminated by <i>&lt;etx&gt;</i>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Max message size
The maximum supported message size (in bytes) for this (de)serializer.

Default is <i>2048</i> (2 KiB).

To avoid memory exhaustion due to a badly behaved client (one that does not adhere to the protocol of the configured serializer), this (de)serializer imposes a maximum message size. If the size is exceeded by an incoming message, an exception will be thrown. The default maximum message size is 2048 bytes, and can be increased by setting the <i>maxMessageSize</i> property.

