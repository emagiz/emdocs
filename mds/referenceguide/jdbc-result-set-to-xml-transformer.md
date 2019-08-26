---
id: jdbc-result-set-to-xml-transformer
title: JDBC result set to XML transformer
sidebar_label: JDBC result set to XML transformer
---
#### Payload transformer that converts results sets created by the JDBC adapters to XML.
Transformer that converts results sets created by the JDBC adapters to XML.

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is defined by the XML schema located at:
<code>classpath:com/emagiz/components/jdbc/emagiz-jdbc-1.0.xsd</code>

<b><i>Example</i></b>

The result of this SQL query (PosgreSQL):
<pre>
SELECT id, active, lastlogin AT TIME ZONE 'UTC' AS lastlogin FROM system$user
</pre>

Results in this XML message:
<pre>
&lt;?xml version="1.0"?&gt;
&lt;jdbc:result-set xmlns:jdbc="http://www.emagiz.com/ns/jdbc/1.0/"&gt;
  &lt;jdbc:row&gt;
    &lt;jdbc:column name="id" value="2"/&gt;
    &lt;jdbc:column name="active" value="true"/&gt;
    &lt;jdbc:column name="lastlogin" value="2011-09-28T16:24:26.709+02:00"/&gt;
  &lt;/jdbc:row&gt;
  &lt;jdbc:row&gt;
    &lt;jdbc:column name="id" value="4"/&gt;
    &lt;jdbc:column name="active" value="false"/&gt;
    &lt;jdbc:column name="lastlogin" value="2011-10-03T14:35:01.447+02:00"/&gt;
  &lt;/jdbc:row&gt;
&lt;/jdbc:result-set&gt;
</pre>

#### Output format
Determines the output format of the transformation.

Usually <code>auto</code> (the default) works fine, but in some cases this can lead to unexpected output. For example, when a JDBC gateway is configured to return a single row, each column in this row will be converted to a separate result set. By using <code>rows</code> this can be prevented, but you'll have to be certain that the result can never actually contain multiple result sets.

Default is <code>auto</code>.

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
id: jdbc-result-set-to-xml-transformer
title: JDBC result set to XML transformer
sidebar_label: JDBC result set to XML transformer
---
#### Payload transformer that converts results sets created by the JDBC adapters to XML.
Transformer that converts results sets created by the JDBC adapters to XML.

The result of this transformation will be a complete, well-formed XML document as a String (the default), XOM document or DOM document. The layout of this document is defined by the XML schema located at:
<code>classpath:com/emagiz/components/jdbc/emagiz-jdbc-1.0.xsd</code>

<b><i>Example</i></b>

The result of this SQL query (PosgreSQL):
<pre>
SELECT id, active, lastlogin AT TIME ZONE 'UTC' AS lastlogin FROM system$user
</pre>

Results in this XML message:
<pre>
&lt;?xml version="1.0"?&gt;
&lt;jdbc:result-set xmlns:jdbc="http://www.emagiz.com/ns/jdbc/1.0/"&gt;
  &lt;jdbc:row&gt;
    &lt;jdbc:column name="id" value="2"/&gt;
    &lt;jdbc:column name="active" value="true"/&gt;
    &lt;jdbc:column name="lastlogin" value="2011-09-28T16:24:26.709+02:00"/&gt;
  &lt;/jdbc:row&gt;
  &lt;jdbc:row&gt;
    &lt;jdbc:column name="id" value="4"/&gt;
    &lt;jdbc:column name="active" value="false"/&gt;
    &lt;jdbc:column name="lastlogin" value="2011-10-03T14:35:01.447+02:00"/&gt;
  &lt;/jdbc:row&gt;
&lt;/jdbc:result-set&gt;
</pre>

#### Output format
Determines the output format of the transformation.

Usually <code>auto</code> (the default) works fine, but in some cases this can lead to unexpected output. For example, when a JDBC gateway is configured to return a single row, each column in this row will be converted to a separate result set. By using <code>rows</code> this can be prevented, but you'll have to be certain that the result can never actually contain multiple result sets.

Default is <code>auto</code>.

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

