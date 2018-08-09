
Adds headers to a message that are not determined by the Message content.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-transformation-chapter.html#header-enricher" target="_blank">Documentation</a>

Use when you need to add headers to a Message.

The Header Enricher also provides helpful <i>Headers</i> to set well-known header names. 

Example:
<code>
error-channel 	ref="applicationErrorChannel"
reply-channel 	ref="quoteReplyChannel"
correlation-id 	value="123"
priority 		value="HIGHEST"
header 		name="bar" ref="someBean"
</code>


Should skip nulls
Specify whether null values, such as might be returned from an expression evaluation, should be skipped. 
Set this to false if a null value should trigger removal of the corresponding header instead.

The default value is true. 


Specifies headers to be added to each message. 

Example:
<code>
error-channel 	ref="applicationErrorChannel"
reply-channel 	ref="quoteReplyChannel"
correlation-id 	value="123"
priority 		value="HIGHEST"
custom header	name="bar" ref="someBean"
</code>


Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>


Id
Name that uniquely identifies this flow component.

<i>Required</i>


Input channel
Channel to consume the input messages from.

<i>Required</i>

