---
id: byte-array-text-length-header--de-serializer
title: Byte array text length header (de)serializer
sidebar_label: Byte array text length header (de)serializer
---
#### Serializes data preceded by an ASCII header indicating the data length
Extension of <code>ByteArrayLengthHeaderSerializer</code> that reads/writes the length header as a textual (ASCII) representation instead of a "normal" binary representation. 

Example: length <code>'255'</code> (with header size <code>'4'</code>) is represented as <code>'0x00 0x32 0x35 0x35'</code>. In the "normal" binary representation this would have been <code>'0x00 0x00 0x00 0xFF'</code>. Note that the use of this textual representation greatly limits the range of possible values compared to the binary representation, possibly resulting in larger header sizes.

#### Header size
Size of the length header in bytes. A header must be at least one byte long.

<i>Required</i>

#### Max message size
The maximum supported message size (in bytes) for this (de)serializer.

Default is <i>2048</i> (2 KiB).

To avoid memory exhaustion due to a badly behaved client (one that does not adhere to the protocol of the configured serializer), this (de)serializer imposes a maximum message size. If the size is exceeded by an incoming message, an exception will be thrown. The default maximum message size is 2048 bytes, and can be increased by setting the <i>maxMessageSize</i> property.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: byte-array-text-length-header--de-serializer
title: Byte array text length header (de)serializer
sidebar_label: Byte array text length header (de)serializer
---
#### Serializes data preceded by an ASCII header indicating the data length
Extension of <code>ByteArrayLengthHeaderSerializer</code> that reads/writes the length header as a textual (ASCII) representation instead of a "normal" binary representation. 

Example: length <code>'255'</code> (with header size <code>'4'</code>) is represented as <code>'0x00 0x32 0x35 0x35'</code>. In the "normal" binary representation this would have been <code>'0x00 0x00 0x00 0xFF'</code>. Note that the use of this textual representation greatly limits the range of possible values compared to the binary representation, possibly resulting in larger header sizes.

#### Header size
Size of the length header in bytes. A header must be at least one byte long.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Max message size
The maximum supported message size (in bytes) for this (de)serializer.

Default is <i>2048</i> (2 KiB).

To avoid memory exhaustion due to a badly behaved client (one that does not adhere to the protocol of the configured serializer), this (de)serializer imposes a maximum message size. If the size is exceeded by an incoming message, an exception will be thrown. The default maximum message size is 2048 bytes, and can be increased by setting the <i>maxMessageSize</i> property.

