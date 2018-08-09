# XML mapping message consumer
#### Message consumer that passes the incoming message payload to the specified Mendix XML-to-domain mapping. 
Message consumer that passes the incoming message payload to the specified Mendix XML-to-domain mapping. 

Compared to the MicroflowInvokingMessageConsumer, this message consumer has slightly better performance, but is very restricted in its use: 
 - message payload must be XML 
 - message headers cannot be passed to Mendix 
 - the XML-to-domain mapping cannot be called with a mapping parameter, so you cannot perform any actions on the mapping result in Mendix 
 - you have no control over the Mendix transaction in which the XML-to-domain mapping is executed 
 - the XML content is stored in memory for better performance, but this increases memory usage (the MicroflowInvokingMessageConsumer stores the XML content in a temp file, which costs less memory but is somewhat slower) 

Unless the performance of the XML mapping is critical and the XML messages are relatively small, consider using a MicroflowInvokingMessageConsumer instead. 

Internally this class uses an XmlToStringTransformer to transform the incoming message payload to an XML string, which is then used as the input for the XML-to-domain mapping. Because of this, all the payload types supported by the XmlToStringTransformer can be used as the input for this message consumer, but the best performance is achieved when the XML payload is already a String.

#### XML-to-domain mapping
Name of the Mendix XML-to-domain mapping to execute on the message payload (must include the module name).

Example: <code>MyModule.MyXmlToDomainMapping</code>

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel to consume messages from.

<i>Required</i>

#### Charset
The name of the character set to be used to encode the string representation of the incoming XML document into a sequence of bytes, which then can be used as the input stream for the Mendix XML-to-domain mapping. 

Default is <code>UTF-8</code>.

#### Logout sessions
Whether to immediately logout the Mendix system session after calling the mapping, or not in which case Mendix will automatically cleanup the session some time later.

From Mendix version 4.8 onwards, setting this to <i>true</i> can potentially prevent out-of-memory exceptions and improve (long term) performance in cases where messages are consumed faster than Mendix can cleanup the sessions.

Default is <i>false</i>.

