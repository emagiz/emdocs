# Standard service activator
Service activator that evaluates a SpEL expression or Groovy script for each incoming message.

While all other <i>service activators</i> have very specific uses, this component is extremely flexible. The downside is that this service activator can be harder to use because it involves scripting.

#### Expression
<i>SpEL</i> expression to be evaluated on each incoming message. If the result of this evaluation is not <code>null</code> and an <i>output channel</i> has been specified, an outgoing message will be created with this result as the payload.

For example, the following expression prints the message payload to the Java standard output stream without generating a reply message: <code>T(System).out.println(payload)</code>

<i>Required</i>

#### Requires reply
Whether this service activator must send a message to the output channel for each incoming message. If enabled and an incoming message doesn't result in an outgoing message, a <code>ReplyRequiredException</code> is thrown instead. 

Default is <i>false</i>.

#### Send timeout
Specify the maximum amount of time in milliseconds to wait when sending a reply message to the output channel.

By default the send will block for one second.

#### Script type
A <i>SpEL expression</i> is a <b>single expression</b> that will be evaluated on the incoming message. This makes it fairly easy to use, but also a bit more limited than the other option. See the <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/spring-framework-reference/html/expressions.html" target="_blank">Spring Expression Language documentation</a> for the exact syntax and options of this language.

A <i>Groovy script</i> is a piece of programming code that is executed for each incoming message, that can in turn use any third-party Java library. This makes it incredibly powerful, but also more complex than the other option. See the <a href="http://docs.groovy-lang.org/docs/groovy-2.4.15/html/documentation/" target="_blank">Groovy language documentation</a> for the exact syntax and options of this language.

Default is <i>SpEL expression</i>.


Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

#### Compile static
Indicates if the target Groovy script should be compiled statically. The <code>@CompileStatic</code> hint is applied for the Groovy compiler.

Default is <i>no</i>.

#### Output channel
Channel where output messages, if this service activator generates any, should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

If <i>requires reply</i> is set to <code>true</code>, specifying an output channel is required. Otherwise this is an optional setting.

#### Location
The location of the Groovy script to be executed on each incoming message. If the return value of the script is not <code>null</code> and an <i>output channel</i> has been specified, an outgoing message will be created with this return value as the payload.

For example: <code>resources/00-012345_myScript.groovy</code>.

Note that you should upload the Groovy script as a resource of this flow (usually with the <i>.groovy</i> filename extension, but this is not required). If you use any (third-party) Java code from your Groovy script, you should also upload these Java libraries (and any dependencies) as resources of this flow. Java libraries must be uploaded as normal (i.e. non-OSGi) <i>.jar</i> files; uploading <i>.java</i> or <i>.class</i> files does not work.
<hr/>Normally, creating an output message is as simple as returning a non-<code>null</code> value in your Groovy script. The framework will then automatically construct an outgoing message with that return value as the payload and with all headers copied from the incoming message.

If you want to customize the outgoing headers as well, you can override this default behaviour by returning a fully constructed <code>org.springframework.messaging.Message</code> from your Groovy script instead. It is highly recommended to use the <code>org.springframework.messaging.support.MessageBuilder</code> helper class for this (see <a href="https://docs.spring.io/spring/docs/4.3.8.RELEASE/javadoc-api/index.html?org/springframework/messaging/support/MessageBuilder.html" target="_blank">Spring API documentation</a>).

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Variables
Comma-delimited pairs of variables and their values that will be passed to the Groovy script. The variable name can apply the <code>-ref</code> suffix, which means to determine a variable value as a bean reference. This attribute isn't mutually exclusive with <i>variable</i> sub-elements (see the <i>advanced</i> tab) and all variables will be merged to one map.

Example:
<code>myVar=staticValue, anotherVar=${example.property}</code>
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

All custom non-ref variables will be passed as a value of type <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

