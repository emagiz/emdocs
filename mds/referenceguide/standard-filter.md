---
id: standard-filter
title: Standard filter
sidebar_label: Standard filter
---

# Standard filter
Filters messages based on the evaluation of a (boolean) SpEL expression or Groovy script for each incoming message. If the expression or script evaluates to <code>true</code> the message will be send to the <i>output channel</i>, otherwise it will be dropped, rejected or send to the <i>discard channel</i>.

While all other <i>filters</i> have very specific uses, this component is extremely flexible. The downside is that this filter can be harder to use because it involves scripting.

#### Expression
A SpEL expression to be evaluated against the input message as its root object. If the expression evaluates to <code>true</code> the message is passed along, if it evaluates to <code>false</code> the message will be dropped.

Some examples:
- <code>payload.matches('^Hello.*$')</code>
- <code>headers.customerID != null</code>
- <code>T(java.lang.Math).random() &lt; 0.5</code>

#### Script type
A <i>SpEL expression</i> is a <b>single expression</b> that will be evaluated on the incoming message. This makes it fairly easy to use, but also a bit more limited than the other option. See the <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/spring-framework-reference/html/expressions.html" target="_blank">Spring Expression Language documentation</a> for the exact syntax and options of this language.

A <i>Groovy script</i> is a piece of programming code that is executed for each incoming message, that can in turn use any third-party Java library. This makes it incredibly powerful, but also more complex than the other option. See the <a href="http://docs.groovy-lang.org/docs/groovy-2.4.15/html/documentation/" target="_blank">Groovy language documentation</a> for the exact syntax and options of this language.

Default is <i>SpEL expression</i>.

#### Throw exception on rejection
Throw an exception when the input message is invalid. This will cause any error handling on the current message flow to trigger.

Note that when set to <code>true</code>, no messages will be send to the <i>discard channel</i>.

#### Discard channel
Channel where messages should be sent if the filter rejects the message. If no discard channel is set, rejected messages are silently dropped.

<i>Optional</i>

#### Location
The location of the Groovy script to be executed on each incoming message. This script must return a value of type <code>Boolean</code>: if the result is <code>true</code> the message will be send to the <i>output channel</i>, if it is <code>false</code> the message will be dropped, rejected or send to the <i>discard channel</i>.

For example: <code>resources/00-012345_myScript.groovy</code>.

Note that you should upload the Groovy script as a resource of this flow (usually with the <i>.groovy</i> filename extension, but this is not required). If you use any (third-party) Java code from your Groovy script, you should also upload these Java libraries (and any dependencies) as resources of this flow. Java libraries must be uploaded as normal (i.e. non-OSGi) <i>.jar</i> files; uploading <i>.java</i> or <i>.class</i> files does not work.


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
id: standard-filter
title: Standard filter
sidebar_label: Standard filter
---

Filters messages based on the evaluation of a (boolean) SpEL expression or Groovy script for each incoming message. If the expression or script evaluates to <code>true</code> the message will be send to the <i>output channel</i>, otherwise it will be dropped, rejected or send to the <i>discard channel</i>.

While all other <i>filters</i> have very specific uses, this component is extremely flexible. The downside is that this filter can be harder to use because it involves scripting.


Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

### _id
Channel where messages should be sent if the filter rejects the message. If no discard channel is set, rejected messages are silently dropped.

<i>Optional</i>

### _id
Channel where messages should be sent if the filter rejects the message. If no discard channel is set, rejected messages are silently dropped.

<i>Optional</i>

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

