---
id: xpath-transformer
title: XPath transformer
sidebar_label: XPath transformer
---
#### Transforms XML messages to simple messages based on the result of an XPath expression
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/xml.html#xpath-transformer" target="_blank">External documentation</a>

The resulting payload message contains the result of the XPath expression evaluation.

Example:
XPath expression : <code>/ns1:one/@type</code>
Namspace prefix : <code>ns1 </code>
Namespace URI:  <code>www.example.org</code>


#### XPath expression
XPath expression 

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>

#### Evaluation type
The result type expected from the XPath evaluation. This will be the payload type of the output Message.

Conversion to the return type follows XPath conversion rules. 

Default when empty is 'STRING_RESULT'.

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
id: xpath-transformer
title: XPath transformer
sidebar_label: XPath transformer
---
#### Transforms XML messages to simple messages based on the result of an XPath expression
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xml.html#xpath-transformer" target="_blank">Documentation</a>

The resulting payload message contains the result of the XPath expression evaluation.

Example:
XPath expression : <code>/ns1:one/@type</code>
Namspace prefix : <code>ns1 </code>
Namespace URI:  <code>www.example.org</code>


#### XPath expression
XPath expression 

<a href="https://www.w3schools.com/xml/xpath_syntax.asp" onclick="window.open('https://www.w3schools.com/xml/xpath_syntax.asp');" target="_blank">XPath syntax reference</a>

#### Evaluation type
The result type expected from the XPath evaluation. This will be the payload type of the output Message.

Conversion to the return type follows XPath conversion rules. 

Default when empty is 'STRING_RESULT'.

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

