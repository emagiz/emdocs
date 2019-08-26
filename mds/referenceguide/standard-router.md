---
id: standard-router
title: Standard router
sidebar_label: Standard Router
---

# Standard router
Routes messages to channels based on the evaluation of a SpEL expression or Groovy script for each incoming message.

While all other <i>routers</i> have very specific uses, this component is extremely flexible. The downside is that this router can be harder to use because it involves scripting.


Maps values of the SpEL expression or Groovy script evaluation to channels.

If the value is not found in a mapping, the router will look for a channel which name matches the value.

Note that if the SpEL expression or Groovy script evaluation returns multiple values (a <code>Collection</code> or comma-separated string), this router will route the message to multiple channels (this duplicates the message).

#### Expression
SpEL expression to be evaluated at runtime; the result is mapped to a channel using the specified <i>value mappings</i>.

However, if no value mappings are present, the expression will evaluate to a channel name directly.

The SpEL expression may also return a <code>Collection</code>, in which case the message will be routed to all channels in that list. This effectively turns this router into a dynamic <i>recipient list router</i>.

<i>Required</i>

#### Script type
A <i>SpEL expression</i> is a <b>single expression</b> that will be evaluated on the incoming message. This makes it fairly easy to use, but also a bit more limited than the other option. See the <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/spring-framework-reference/html/expressions.html" target="_blank">Spring Expression Language documentation</a> for the exact syntax and options of this language.

A <i>Groovy script</i> is a piece of programming code that is executed for each incoming message, that can in turn use any third-party Java library. This makes it incredibly powerful, but also more complex than the other option. See the <a href="http://docs.groovy-lang.org/docs/groovy-2.4.15/html/documentation/" target="_blank">Groovy language documentation</a> for the exact syntax and options of this language.

Default is <i>SpEL expression</i>.

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Location
The location of the Groovy script to be executed on each incoming message. This script should return a <code>String</code> value that will be mapped to a channel using the specified <i>value mappings</i>.

However, if no value mappings are present, the result will evaluate to a channel name directly.

The Groovy script may also return a <code>Collection&lt;String&gt;</code> or a comma-separated <code>String</code>, in which case the message will be routed to all channels in that list. This effectively turns this router into a dynamic <i>recipient list router</i>.

For example: <code>resources/00-012345_myScript.groovy</code>.

Note that you should upload the Groovy script as a resource of this flow (usually with the <i>.groovy</i> filename extension, but this is not required). If you use any (third-party) Java code from your Groovy script, you should also upload these Java libraries (and any dependencies) as resources of this flow. Java libraries must be uploaded as normal (i.e. non-OSGi) <i>.jar</i> files; uploading <i>.java</i> or <i>.class</i> files does not work.

#### Resolution required
If set to <i>yes</i> and channel resolution fails, a <code>MessageDeliveryException</code> is thrown. If set to <i>no</i> such failures are (silently) ignored, possibly resulting in the router resolving zero channels.

Channel resolution failure means that the routing criteria cannot be successfully resolved, for example when a <i>header value router</i> tries to route a message with a header value that is not specified in the mappings, or when any of the XPath evaluation results of an <i>XPath router</i> cannot be found in the mappings.

Note that this behaviour does <b>not</b> apply to cases where resolving the routing criteria (successfully) results in zero channels, for example when a <i>header value router</i> tries to route a message that doesn't contain the specified message header, or when the evaluation of the XPath expression by an <i>XPath router</i> produces no results.

Please be aware that instead of suppressing these exceptions, it is also possible to explicitly drop certain messages by routing them to the <i>nullChannel</i>.

Default is <i>yes</i>.

#### Ignore send failures
If set to <i>yes</i>, failures to send to a message channel will be ignored. If set to <i>no</i>, a <code>MessageDeliveryException</code> will be thrown instead, and if the router resolves more than one channel, any subsequent channels will not receive the message.

Please be aware that when using direct channels (single threaded), send-failures can be caused by exceptions thrown by components much further down-stream.

Also note that this behaviour does <b>not</b> apply to the the optional <i>default output channel</i>.

Default is <i>no</i>.

#### Apply sequence
Specify whether sequence number and size headers should be added to each message.

Default is <i>no</i>.

#### Timeout
Specify the maximum amount of time in milliseconds to wait when sending messages to the target message channels.

By default the send will block indefinitely.

#### Default output channel
The default channel where messages should be sent if the router didn't send the message to any of the normal output channels.

If no default output channel is provided and the router didn't send the message to any of the normal output channels a <code>MessageDeliveryException</code> is thrown. If you would like to silently drop those messages instead, use the <i>nullChannel</i> as the default output channel.
<hr/>A router might not be able to send a message to any of the normal output channels in the following cases:

<b><i>resolving the routing criteria resulted in zero channels</i></b>
For example, when a <i>header value router</i> tries to route a message that doesn't contain the specified message header, or when the evaluation of the XPath expression by an <i>XPath router</i> produces no results.

<b><i>resolving the routing criteria failed and 'resolution required' is disabled</i></b>
For example, when a <i>header value router</i> tries to route a message with a header value that is not specified in the mappings, or when all results of the evaluation of the XPath expression by an <i>XPath router</i> cannot be found in the mappings.

<b><i>all send attempts failed and 'ignore send failures' is enabled</i></b>
For example, when every normal output channel connects to a down-stream filter that rejects the message using the <i>throw exception on rejection</i> option (the "selective consumer" pattern).

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>


Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

#### Compile static
Indicates if the target Groovy script should be compiled statically. The <code>@CompileStatic</code> hint is applied for the Groovy compiler.

Default is <i>no</i>.

#### Variables
Comma-delimited pairs of variables and their values that will be passed to the Groovy script. The variable name can apply the <code>-ref</code> suffix, which means to determine a variable value as a bean reference. This attribute isn't mutually exclusive with <i>variable</i> sub-elements (see the <i>advanced</i> tab) and all variables will be merged to one map.

Example:
<code>myVar=staticValue, anotherVar=${example.property}</code>
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

---
id: standard-router
title: Standard router
sidebar_label: Standard router
---

Routes messages to channels based on the evaluation of a SpEL expression or Groovy script for each incoming message.

While all other <i>routers</i> have very specific uses, this component is extremely flexible. The downside is that this router can be harder to use because it involves scripting.


Maps values of the SpEL expression or Groovy script evaluation to channels.

If the value is not found in a mapping, the router will look for a channel which name matches the value.

Note that if the SpEL expression or Groovy script evaluation returns multiple values (a <code>Collection</code> or comma-separated string), this router will route the message to multiple channels (this duplicates the message).

### _id
Channel to consume the input messages from.

<i>Required</i>

### _id
Channel to consume the input messages from.

<i>Required</i>

### _id
The default channel where messages should be sent if the router didn't send the message to any of the normal output channels.

If no default output channel is provided and the router didn't send the message to any of the normal output channels a <code>MessageDeliveryException</code> is thrown. If you would like to silently drop those messages instead, use the <i>nullChannel</i> as the default output channel.
<hr/>A router might not be able to send a message to any of the normal output channels in the following cases:

<b><i>resolving the routing criteria resulted in zero channels</i></b>
For example, when a <i>header value router</i> tries to route a message that doesn't contain the specified message header, or when the evaluation of the XPath expression by an <i>XPath router</i> produces no results.

<b><i>resolving the routing criteria failed and 'resolution required' is disabled</i></b>
For example, when a <i>header value router</i> tries to route a message with a header value that is not specified in the mappings, or when all results of the evaluation of the XPath expression by an <i>XPath router</i> cannot be found in the mappings.

<b><i>all send attempts failed and 'ignore send failures' is enabled</i></b>
For example, when every normal output channel connects to a down-stream filter that rejects the message using the <i>throw exception on rejection</i> option (the "selective consumer" pattern).

### _id
The default channel where messages should be sent if the router didn't send the message to any of the normal output channels.

If no default output channel is provided and the router didn't send the message to any of the normal output channels a <code>MessageDeliveryException</code> is thrown. If you would like to silently drop those messages instead, use the <i>nullChannel</i> as the default output channel.
<hr/>A router might not be able to send a message to any of the normal output channels in the following cases:

<b><i>resolving the routing criteria resulted in zero channels</i></b>
For example, when a <i>header value router</i> tries to route a message that doesn't contain the specified message header, or when the evaluation of the XPath expression by an <i>XPath router</i> produces no results.

<b><i>resolving the routing criteria failed and 'resolution required' is disabled</i></b>
For example, when a <i>header value router</i> tries to route a message with a header value that is not specified in the mappings, or when all results of the evaluation of the XPath expression by an <i>XPath router</i> cannot be found in the mappings.

<b><i>all send attempts failed and 'ignore send failures' is enabled</i></b>
For example, when every normal output channel connects to a down-stream filter that rejects the message using the <i>throw exception on rejection</i> option (the "selective consumer" pattern).


Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

