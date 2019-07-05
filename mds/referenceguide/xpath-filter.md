---
id: xpath-filter
title: XPath filter
sidebar_label: XPath filter
---
#### Filters XML messages based on an XPath expression.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xml.html#xml-xpath-filter" target="_blank">Documentation</a>

Defines an XPath-based message filter.

If the XPath expression will evaluate to a boolean, no configuration attributes are required. If the XPath expression will evaluate to a string, a <i>match value</i> should be provided against which the evaluation result will be matched.

There are three options for the <i>match value</i>: <i>exact</i>, <i>case-insensitive</i> and <i>regex</i>. These correspond to the <i>equals</i>, <i>equals-ignore-case</i> and <i>matches</i> operations on <code>java.lang.String</code>, respectively. When providing a <i>match type</i> value of <i>regex</i>, the value provided in <i>match value</i> must be a valid regular expression.

#### Match value
String value to be matched against the XPath evaluation result.

If this is not provided, then the XPath evaluation <b>must</b> produce a boolean result directly.

#### Match type
Type of match to apply between the XPath evaluation result and the <i>match value</i>.

<code>exact</code> - case-sensitive string comparison
<code>case-insensitive</code> - case-insensitive string comparison
<code>regex</code> - comparison using a regular expression

Default is <code>exact<code>.


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

#### Throw exception on rejection
Throw an exception when the input message is invalid. This will cause any error handling on the current message flow to trigger.

Note that when set to <code>true</code>, no messages will be send to the <i>discard channel</i>.


XPath expression that returns a value (boolean or string) used for filtering the message. In case of a boolean value, <code>true</code> accepts the message and <code>false</code> discards it. In case of a string value, this decision depends on the value of the <i>match value</i> and <i>match type</i> settings.

<i>Required</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>

#### Discard channel
Channel where messages should be sent if the filter rejects the message. If no discard channel is set, rejected messages are silently dropped.

<i>Optional</i>

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

