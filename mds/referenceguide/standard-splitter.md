---
id: standard-splitter
title: Standard Splitter
sidebar_label: Standard Splitter
---

# Standard splitter
Splits incoming messages into multiple outgoing messages in one of the following ways:
- by splitting list-based messages into its containing items
- by tokenizing string-based messages using delimiter characters
- by executing a SpEL expression that splits the message
- by executing a Groovy script that performs the splitting operation

While all other <i>splitters</i> have very specific uses, this component is extremely flexible. The downside is that this splitter can be harder to use because it involves scripting.

#### Requires reply
Whether this splitter must send at least one message to the output channel for each incoming message. If enabled and an incoming message doesn't result in at least one outgoing message, a <code>ReplyRequiredException</code> is thrown instead. 

Default is <i>no</i>.

#### Delimiters
One or more delimiters (as a single string value, for example <code>,;:</code>) for splitting string payloads.

Only used if the payload of the incoming message is of type <code>String</code> to tokenize that string. Otherwise (this includes <code>String</code> payloads when not specifying any <i>delimiters</i>) messages are handled as follows: for payloads of types <code>Collection&lt;?&gt;</code>, <code>Iterable&lt;?&gt;</code>, <code>Iterator&lt;?&gt;</code> and arrays an output message is created for each item, while for all other payloads the message is "split" into a single message.

<i>Optional</i>

#### Expression
<i>SpEL</i> expression to be evaluated on each incoming message. The result of this evaluation will be used as the payload for the outgoing messages as follows (if no expression is specified, these rules are applied to the unaltered payload of the input message):
- if the result is an array or <code>Collection</code>, each entry will be converted into a separate message
- if the result is <code>null</code>, no output messages are created
- in all other cases, the result is converted into a single output message

An example of a simple SpEL expression that splits string messages using a regular expression:
<code>payload.split('\n')</code>

An example of a more complex SpEL expression that splits a comma-separated string while filtering out empty values:
<code>payload.split(',').?[!#this.trim().isEmpty()]</code>

#### Script type
<i>None</i> indicates that default splitting behaviour is applied: simply splitting list-based messages into one message per item in that list or splitting string-based messages using a delimiter.

A <i>SpEL expression</i> is a <b>single expression</b> that will be evaluated on the incoming message. This makes it fairly easy to use, but also a bit more limited than the other option. See the <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/spring-framework-reference/html/expressions.html" target="_blank">Spring Expression Language documentation</a> for the exact syntax and options of this language.

A <i>Groovy script</i> is a piece of programming code that is executed for each incoming message, that can in turn use any third-party Java library. This makes it incredibly powerful, but also more complex than the other option. See the <a href="http://docs.groovy-lang.org/docs/groovy-2.4.15/html/documentation/" target="_blank">Groovy language documentation</a> for the exact syntax and options of this language.

Default is <i>none</i>.

#### Location
The location of the Groovy script to be executed on each incoming message. This script should return a value of type <code>Collection&lt;?&gt;</code>, <code>Iterable&lt;?&gt;</code>, <code>Iterator&lt;?&gt;</code> or an array: an outgoing message will be created for each item in this list with that item as the payload, which will then be send to the <i>output channel</i>. This is done one item at a time, therefore when returning an <code>Iterable&lt;?&gt;</code> or <code>Iterator&lt;?&gt;</code> you can effectively build a "streaming" splitter. A downside might be that the <code>sequenceSize</code> header in these cases will always have value <code>0</code>. Using an array or <code>Collection&lt;?&gt;</code> does not have this disadvantage, but requires all messages to fit in memory at the same time.

For example: <code>resources/00-012345_myScript.groovy</code>.

Note that you should upload the Groovy script as a resource of this flow (usually with the <i>.groovy</i> filename extension, but this is not required). If you use any (third-party) Java code from your Groovy script, you should also upload these Java libraries (and any dependencies) as resources of this flow. Java libraries must be uploaded as normal (i.e. non-OSGi) <i>.jar</i> files; uploading <i>.java</i> or <i>.class</i> files does not work.
<hr/>Normally, creating output messages is as simple as returning a non-<code>null</code> values as items in a <code>Collection&lt;?&gt;</code>, <code>Iterable&lt;?&gt;</code>, <code>Iterator&lt;?&gt;</code> or array in your Groovy script. The framework will then automatically construct an outgoing message for each item in that list with the item as the payload and with all headers copied from the incoming message.

If you want to customize the outgoing headers as well, you can override this default behaviour by returning fully constructed <code>org.springframework.messaging.Message</code> objects in a <code>Collection&lt;?&gt;</code>, <code>Iterable&lt;?&gt;</code>, <code>Iterator&lt;?&gt;</code> or array from your Groovy script instead. It is highly recommended to use the <code>org.springframework.messaging.support.MessageBuilder</code> helper class for this (see <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/javadoc-api/index.html?org/springframework/messaging/support/MessageBuilder.html" target="_blank">Spring API documentation</a>).

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Variables
Comma-delimited pairs of variables and their values that will be passed to the Groovy script. The variable name can apply the <code>-ref</code> suffix, which means to determine a variable value as a bean reference. This attribute isn't mutually exclusive with <i>variable</i> sub-elements (see the <i>advanced</i> tab) and all variables will be merged to one map.

Example:
<code>myVar=staticValue, anotherVar=${example.property}</code>
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Apply sequence
Set this flag to <i>no</i> to prevent adding sequence related headers in this splitter. This can be convenient in cases where the set sequence numbers conflict with downstream custom aggregations. When <i>yes</i>, existing correlation and sequence related headers (<code>correlationId</code>, <code>sequenceNumber</code> and <code>sequenceSize</code>) are pushed onto a stack; downstream components, such as aggregators may pop the stack to revert the existing headers after aggregation.

Default is <i>yes</i>.


Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

#### Compile static
Indicates if the target Groovy script should be compiled statically. The <code>@CompileStatic</code> hint is applied for the Groovy compiler.

Default is <i>no</i>.

---
id: standard-splitter
title: Standard splitter
sidebar_label: Standard splitter
---

Splits incoming messages into multiple outgoing messages in one of the following ways:
- by splitting list-based messages into its containing items
- by tokenizing string-based messages using delimiter characters
- by executing a SpEL expression that splits the message
- by executing a Groovy script that performs the splitting operation

While all other <i>splitters</i> have very specific uses, this component is extremely flexible. The downside is that this splitter can be harder to use because it involves scripting.


Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

### _id
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

### _id
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

### _id
Channel to consume the input messages from.

<i>Required</i>

### _id
Channel to consume the input messages from.

<i>Required</i>

