---
id: xpath-splitter
title: XPath splitter
sidebar_label: XPath splitter
---
#### Uses an XPath expression to split a message into multiple messages.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/xml.html#xpath-splitting" target="_blank">External documentation</a>

The splitter uses the provided <i>XPath expression</i> to split the payload into a number of nodes. By default this will result in each Node becoming the payload of a new message. 

Where it is preferred that each message be a <i>XML Document</i> the <i>Create documents</i> flag can be set. Where a <i>String</i> payload is passed in the payload will be converted then split before being converted back to a number of <i>String</i> messages. 

This splitter supports messages with either <i>String</i> or <i>XML document</i> payloads.

#### Create documents
Set this flag to <code>true</code> to convert each resuling <code>Node</code> to a <code>Document</code> before sending replies from this splitter.

Default is <code>false</code>.

#### Iterator
The iterator mode: <code>true</code> (default) to return an <code>java.util.Iterator</code> for splitting the payload, <code>false</code> to return a <code>java.util.List</code>. 

Be aware that in iterator mode the <code>sequenceSize</code> header will always be set to <code>0</code>, because the splitter does not have access to the underlying items.

Note: the list contains transformed nodes whereas with the iterator each node is transformed while iterating.

Default is <code>true</code>.


Namespace prefix of the XML nodes in the XPath expression

<i>Optional, but required when namespace URI is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>


Namespace URI of the XML nodes in the XPath expression.

<i>Optional, but required when namespace prefix is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>


XPath expression that returns a value (boolean or string) used for filtering the message. In case of a boolean value, <code>true</code> accepts the message and <code>false</code> discards it. In case of a string value, this decision depends on the value of the <i>match value</i> and <i>match type</i> settings.

<i>Required</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>

#### Apply sequence
Set this flag to <code>false</code> to prevent adding sequence related headers in this splitter. This can be convenient in cases where the set sequence numbers conflict with downstream custom aggregations. When <code>true</code>, existing correlation and sequence related headers (<code>correlationId</code>, <code>sequenceNumber</code> and <code>sequenceSize</code>) are pushed onto a stack; downstream components, such as aggregators may pop the stack to revert the existing headers after aggregation.

Default is <code>true</code>.

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
id: xpath-splitter
title: XPath splitter
sidebar_label: XPath splitter
---
#### Uses an XPath expression to split a message into multiple messages.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xml.html#xpath-splitting" target="_blank">Documentation</a>

The splitter uses the provided <i>XPath expression</i> to split the payload into a number of nodes. By default this will result in each Node becoming the payload of a new message. 

Where it is preferred that each message be a <i>XML Document</i> the <i>Create documents</i> flag can be set. Where a <i>String</i> payload is passed in the payload will be converted then split before being converted back to a number of <i>String</i> messages. 

This splitter supports messages with either <i>String</i> or <i>XML document</i> payloads.

#### Create documents
Set this flag to <code>true</code> to convert each resuling <code>Node</code> to a <code>Document</code> before sending replies from this splitter.

Default is <code>false</code>.

#### Iterator
The iterator mode: <code>true</code> (default) to return an <code>java.util.Iterator</code> for splitting the payload, <code>false</code> to return a <code>java.util.List</code>. 

Be aware that in iterator mode the <code>sequenceSize</code> header will always be set to <code>0</code>, because the splitter does not have access to the underlying items.

Note: the list contains transformed nodes whereas with the iterator each node is transformed while iterating.

Default is <code>true</code>.


Namespace prefix of the XML nodes in the XPath expression

<i>Optional, but required when namespace URI is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>


XPath expression that returns a value (boolean or string) used for filtering the message. In case of a boolean value, <code>true</code> accepts the message and <code>false</code> discards it. In case of a string value, this decision depends on the value of the <i>match value</i> and <i>match type</i> settings.

<i>Required</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>


Namespace URI of the XML nodes in the XPath expression.

<i>Optional, but required when namespace prefix is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>

#### Apply sequence
Set this flag to <code>false</code> to prevent adding sequence related headers in this splitter. This can be convenient in cases where the set sequence numbers conflict with downstream custom aggregations. When <code>true</code>, existing correlation and sequence related headers (<code>correlationId</code>, <code>sequenceNumber</code> and <code>sequenceSize</code>) are pushed onto a stack; downstream components, such as aggregators may pop the stack to revert the existing headers after aggregation.

Default is <code>true</code>.

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

