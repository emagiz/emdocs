
Transformer for converting images to different formats, e.g. from GIF to JPEG. 
Transformer for converting images to different formats, e.g. from GIF to JPEG. 

The payload of the message to transform must be an image (in one of the supported formats), represented as one of:
 - a byte array containing the raw image bytes 
 - a String containing the Base64 encoded image bytes

The resulting output image will use the same representation as the given input, i.e. byte[] or Base64 String. The actual transformation always works on a byte[] internally, so when a Base64 String representation is used, a Base64DecodingTransformer and a Base64EncodingTransformer are used to convert to/from this internal format. These additional transformations will decrease the performance and increase the memory usage somewhat, so working with byte arrays instead (and doing the Base64 transformations further up- or downstream in the message flow) should be considered when performance is important. 

Formats supported for the input and output images depend on the image readers and writers registered with the Java Image I/O API – see ImageIO.getReaderFormatNames() and ImageIO.getWriterFormatNames() – but at least the formats BMP, GIF, JPEG, PNG and TIFF are supported when using a default eMagiz installation.


Format
The format to transform the image to (i.e. the output format). 

Default is 'PNG'.


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

