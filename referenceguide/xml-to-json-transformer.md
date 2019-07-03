---
id: xml-to-json-transformer
title: XML to JSON transformer
sidebar_label: XML to JSON transformer
---
#### Payload transformer that converts XML messages to JSON.
Transformer that converts XML messages to a JSON string.

The input of this transformation must be a complete, well-formed XML document as a XOM Document, DOM Document, String, File, Reader or InputStream. This document must validate against the XML schema located at:
<code>classpath:com/emagiz/components/json/emagiz-json-1.0.xsd</code>

<b><i>Example</i></b>

This XML message:
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

Results in this JSON message:
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

