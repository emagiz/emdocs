Standard transformer
Transforms messages by executing a SpEL expression or Groovy script on each incoming message.

While all other <i>transformers</i> have very specific uses, this component is extremely flexible. The downside is that this transformer can be harder to use because it involves scripting.

Expression
<i>SpEL</i> expression to be evaluated on each incoming message. The result of this evaluation will be used as the payload for the outgoing message.


<i><b>Examples</b></i>

An example of a simple SpEL expression that converts string messages to upper case:
<pre>
payload.toUpperCase()
</pre>

An example of a more complex SpEL expression that replaces all <code>[%CurrentDateTime%]</code> tokens with the actual current date/time:
<pre>
payload.replace('[%CurrentDateTime%]', T(org.joda.time.format.ISODateTimeFormat).dateTime().print(T(System).currentTimeMillis()))
</pre>

Script type
A <i>SpEL expression</i> is a <b>single expression</b> that will be evaluated on the incoming message. This makes it fairly easy to use, but also a bit more limited than the other option. See the <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/spring-framework-reference/html/expressions.html" target="_blank">Spring Expression Language documentation</a> for the exact syntax and options of this language.

A <i>Groovy script</i> is a piece of programming code that is executed for each incoming message, that can in turn use any third-party Java library. This makes it incredibly powerful, but also more complex than the other option. See the <a href="http://docs.groovy-lang.org/docs/groovy-2.4.15/html/documentation/" target="_blank">Groovy language documentation</a> for the exact syntax and options of this language.

Default is <i>SpEL expression</i>.


Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

Compile static
Indicates if the target Groovy script should be compiled statically. The <code>@CompileStatic</code> hint is applied for the Groovy compiler.

Default is <i>no</i>.

Location
The location of the Groovy script to be executed on each incoming message. This script must return a non-<code>null</code> value: an outgoing message will be created with this return value as the payload, which will then be send to the <i>output channel</i>.

For example: <code>resources/00-012345_myScript.groovy</code>.

Note that you should upload the Groovy script as a resource of this flow (usually with the <i>.groovy</i> filename extension, but this is not required). If you use any (third-party) Java code from your Groovy script, you should also upload these Java libraries (and any dependencies) as resources of this flow. Java libraries must be uploaded as normal (i.e. non-OSGi) <i>.jar</i> files; uploading <i>.java</i> or <i>.class</i> files does not work.
<hr/>Normally, creating an output message is as simple as returning a non-<code>null</code> value in your Groovy script. The framework will then automatically construct an outgoing message with that return value as the payload and with all headers copied from the incoming message.

If you want to customize the outgoing headers as well, you can override this default behaviour by returning a fully constructed <code>org.springframework.messaging.Message</code> from your Groovy script instead. It is highly recommended to use the <code>org.springframework.messaging.support.MessageBuilder</code> helper class for this (see <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/javadoc-api/index.html?org/springframework/messaging/support/MessageBuilder.html" target="_blank">Spring API documentation</a>).

Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

Variables
Comma-delimited pairs of variables and their values that will be passed to the Groovy script. The variable name can apply the <code>-ref</code> suffix, which means to determine a variable value as a bean reference. This attribute isn't mutually exclusive with <i>variable</i> sub-elements (see the <i>advanced</i> tab) and all variables will be merged to one map.

Example:
<code>myVar=staticValue, anotherVar=${example.property}</code>
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

Input channel
Channel to consume the input messages from.

<i>Required</i>

Id
Name that uniquely identifies this flow component.

<i>Required</i>

