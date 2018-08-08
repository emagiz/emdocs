
Defines an XPath expression.
Example:
XPath expression : <code>/ns1:one/@type</code>
Namspace prefix : <code>ns1 </code>
Namespace URI: <code>www.example.org</code>

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>



Id
Name that uniquely identifies this flow component.

<i>Required</i>


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


Namespace prefix of the XML nodes in the XPath expression

<i>Optional, but required when namespace URI is set</i>

Example:
XPath expression : <code>/ns1:one/@type</code>
Namespace prefix : <code>ns1</code>
Namespace URI: <code>http://www.example.org</code>

<a href="https://www.w3schools.com/xml/xml_namespaces.asp" onclick="window.open('https://www.w3schools.com/xml/xml_namespaces.asp');" target="_blank">XML namespace reference</a>

