# Parameter map to XML transformer
#### Payload transformer that transforms a parameter map as returned by a Http servlet request to XML.
Payload transformer that transforms a parameter map as returned by HttpServletRequest.getParameterMap() to XML.

The result of this transformation will be a complete, well-formed XML document as a String, XOM document or DOM document. For the layout of this document, see the example below.

<b>Example</b>
The parameter map generated for these URI parameters:
<pre>  ...?param1=value1&amp;param2=value2.1&amp;param2=value2.2</pre>
will result in this XML document:
<pre>
&lt;?xml version=&quot;1.0&quot;?&gt;
&lt;http:parameter-map xmlns:http=&quot;http://www.emagiz.com/ns/http/1.0/&quot;&gt;
   &lt;http:parameter name=&quot;param1&quot; value=&quot;value1&quot; /&gt;
   &lt;http:parameter name=&quot;param2&quot;&gt;
      &lt;http:value&gt;value2.1&lt;/http:value&gt;
      &lt;http:value&gt;value2.2&lt;/http:value&gt;
   &lt;/http:parameter&gt;
&lt;/http:parameter-map&gt;
</pre>

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Result type
Sets the result type (<code>XomDocument</code>, <code>DomDocument</code> or <code>String</code>) for the transformation. 

Default is <code>String</code>.


#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

