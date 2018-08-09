# XPath header enricher
#### Adds headers to messages based on XPath expressions. 
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-transformation-chapter.html#header-enricher" target="_blank">Documentation</a>

Defines a Header Enricher Message Transformer that evaluates XPath expressions against the message payload and inserts the result of the evaluation into a messsage header.

#### Should skip nulls
Specify whether null values, such as might be returned from an expression evaluation, should be skipped. 
Set this to false if a null value should trigger removal of the corresponding header instead.

The default value is true. 


Name/XPath-expression pairs that specify the headers.

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

