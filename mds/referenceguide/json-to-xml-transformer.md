---
id: json-to-xml-transformer
title: JSON to XML transformer
sidebar_label: JSON to XML transformer
---
#### Payload transformer that converts JSON messages to XML. 
Transformer that converts JSON string messages to XML.

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is defined by the XML schema located at:
<code>classpath:com/emagiz/components/json/emagiz-json-1.0.xsd</code>

<b><i>Example</i></b>

This JSON message:
<pre>
{
   "description" : "This is a JSON example.",
   "contents"    : [
      1234,
      true,
      null,
      {
         "field1" : -1.0,
         "field2" : []
      }
   ]
}
</pre>

Results in this XML message:
<pre>
&lt;?xml version="1.0"?&gt;
&lt;json:object xmlns:json="http://www.emagiz.com/ns/json/1.0/"&gt;
   &lt;json:string name="description" value="This is a JSON example."/&gt;
   &lt;json:array name="contents"&gt;
      &lt;json:number value="1234"/&gt;
      &lt;json:boolean value="true"/&gt;
      &lt;json:null/&gt;
      &lt;json:object&gt;
         &lt;json:number name="field1" value="-1.0"/&gt;
         &lt;json:array name="field2"/&gt;
      &lt;/json:object&gt;
   &lt;/json:array&gt;
&lt;/json:object&gt;
</pre>

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
id: json-to-xml-transformer
title: JSON to XML transformer
sidebar_label: JSON to XML transformer
---
#### Payload transformer that converts JSON messages to XML. 
Transformer that converts JSON string messages to XML.

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is defined by the XML schema located at:
<code>classpath:com/emagiz/components/json/emagiz-json-1.0.xsd</code>

<b><i>Example</i></b>

This JSON message:
<pre>
{
   "description" : "This is a JSON example.",
   "contents"    : [
      1234,
      true,
      null,
      {
         "field1" : -1.0,
         "field2" : []
      }
   ]
}
</pre>

Results in this XML message:
<pre>
&lt;?xml version="1.0"?&gt;
&lt;json:object xmlns:json="http://www.emagiz.com/ns/json/1.0/"&gt;
   &lt;json:string name="description" value="This is a JSON example."/&gt;
   &lt;json:array name="contents"&gt;
      &lt;json:number value="1234"/&gt;
      &lt;json:boolean value="true"/&gt;
      &lt;json:null/&gt;
      &lt;json:object&gt;
         &lt;json:number name="field1" value="-1.0"/&gt;
         &lt;json:array name="field2"/&gt;
      &lt;/json:object&gt;
   &lt;/json:array&gt;
&lt;/json:object&gt;
</pre>

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

