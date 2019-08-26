---
id: mendix-filedocument-ws-request-transformer
title: Mendix FileDocument WS request transformer
sidebar_label: Mendix FileDocument WS request transformer
---
#### Creates web service request messages for passing the payload to Mendix as a System.FileDocument object.
Transformer that converts the incoming message payload into a Mendix web service request that contains this payload as a <i>Base64</i> encoded string. Such web service requests are compatible with a Mendix published web service operation that has the <code>Contents</code> member of a <code>System.FileDocument</code> entity as its only parameter. 

This is useful in two situations: 
 - Passing the contents of any file to Mendix, so it can be stored as a <code>System.FileDocument</code>. 
 - Passing an XML document to a Mendix web service, so it can be used in an <i>XML-to-domain mapping</i> (a workaround for creating "contract first" web services in Mendix). 

The output of this transformation is an XML document that looks like the following:
<pre>
&lt;?xml version="1.0"?&gt;
&lt;ns:OperationName xmlns:ns="http://www.example.org/"&gt;
  &lt;ParameterName&gt;
    &lt;MemberName&gt;PD94bWwgdmVyc2lvbj0iMS4wIj8+PHRlc3QvPg==&lt;/MemberName&gt;
  &lt;/ParameterName&gt;
&lt;/ns:OperationName&gt;
</pre>

#### Namespace
The <i>Target namespace</i> of the Mendix <i>Published Web Service</i> these web service requests are intended for.

#### Operation name
The <i>WSDL Name</i> of the Mendix <i>Published Operation</i> these web service requests are intended for.

#### Parameter name
The <i>WSDL Name</i> of the (single) Mendix <i>Parameter</i> (of type <code>System.FileDocument</code>) these web service requests are intended for.

#### Member name
The <i>WSDL name</i> of the (single) Mendix <i>Member</i> (of type <code>Binary</code>) these web service requests are intended for.

<b>Warning:</b>
Due to a bug in Mendix, using any other <i>WSDL name</i> than the default (<code>Contents</code>) will cause the web service to skip mapping the actual <i>FileDocument</i> contents.

#### Charset
The name of the <i>charset</i> to be used to encode the string representation of the incoming XML document or string payload into a sequence of bytes, which is then encoded as a <i>Base64</i> string value to be passed to the Mendix web service. 

If the payload of the incoming message is already in byte form (i.e. a <code>byte[]</code>), this property is not used. 

Default is <code>UTF-8</code>.

#### Result type
Sets the result type (<code>XomDocument</code>, <code>DomDocument</code> or <code>String</code>) for the transformation. 

Default is <code>String</code>.


#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: mendix-filedocument-ws-request-transformer
title: Mendix FileDocument WS request transformer
sidebar_label: Mendix FileDocument WS request transformer
---
#### Creates web service request messages for passing the payload to Mendix as a System.FileDocument object.
Transformer that converts the incoming message payload into a Mendix web service request that contains this payload as a <i>Base64</i> encoded string. Such web service requests are compatible with a Mendix published web service operation that has the <code>Contents</code> member of a <code>System.FileDocument</code> entity as its only parameter. 

This is useful in two situations: 
 - Passing the contents of any file to Mendix, so it can be stored as a <code>System.FileDocument</code>. 
 - Passing an XML document to a Mendix web service, so it can be used in an <i>XML-to-domain mapping</i> (a workaround for creating "contract first" web services in Mendix). 

The output of this transformation is an XML document that looks like the following:
<pre>
&lt;?xml version="1.0"?&gt;
&lt;ns:OperationName xmlns:ns="http://www.example.org/"&gt;
  &lt;ParameterName&gt;
    &lt;MemberName&gt;PD94bWwgdmVyc2lvbj0iMS4wIj8+PHRlc3QvPg==&lt;/MemberName&gt;
  &lt;/ParameterName&gt;
&lt;/ns:OperationName&gt;
</pre>

#### Namespace
The <i>Target namespace</i> of the Mendix <i>Published Web Service</i> these web service requests are intended for.

#### Operation name
The <i>WSDL Name</i> of the Mendix <i>Published Operation</i> these web service requests are intended for.

#### Parameter name
The <i>WSDL Name</i> of the (single) Mendix <i>Parameter</i> (of type <code>System.FileDocument</code>) these web service requests are intended for.

#### Member name
The <i>WSDL name</i> of the (single) Mendix <i>Member</i> (of type <code>Binary</code>) these web service requests are intended for.

<b>Warning:</b>
Due to a bug in Mendix, using any other <i>WSDL name</i> than the default (<code>Contents</code>) will cause the web service to skip mapping the actual <i>FileDocument</i> contents.

#### Charset
The name of the <i>charset</i> to be used to encode the string representation of the incoming XML document or string payload into a sequence of bytes, which is then encoded as a <i>Base64</i> string value to be passed to the Mendix web service. 

If the payload of the incoming message is already in byte form (i.e. a <code>byte[]</code>), this property is not used. 

Default is <code>UTF-8</code>.

#### Result type
Sets the result type (<code>XomDocument</code>, <code>DomDocument</code> or <code>String</code>) for the transformation. 

Default is <code>String</code>.


#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

