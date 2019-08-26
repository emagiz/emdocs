---
id: custom-error-message-activator
title: Custom error message activator
sidebar_label: Custom error message activator
---
#### Generates and throws a custom error message each time a message arrives.
Generates and throws a <code>CustomErrorMessage</code> each time a message arrives. The text of the error message is dynamically created using a SpEL expression that is evaluated on the incoming message.

This can be used to trigger the error handling of the message flow with an error message that contains useful information for locating the problem. For example, when throwing a custom error message in a flow that is exposed as a web service, this custom error is send back to the caller as a <i>SOAP fault</i>.

Note that this <i>service activator</i> will never produce any output messages.

#### Expression
<i>SpEL</i> expression to be evaluated on each incoming message. The result of this evaluation will be used as the text for the custom error message.

<i>Required</i>


<i><b>Examples</b></i>

An example of a simple SpEL expression that always results in the same (static) message:
<pre>
'Oops, something went wrong!'
</pre>

An example of a more complex SpEL expression that uses header information from the input message:
<pre>
'Request for user "' + (headers['example_user'] ?: 'anonymous') + '" failed.'
</pre>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: custom-error-message-activator
title: Custom error message activator
sidebar_label: Custom error message activator
---
#### Generates and throws a custom error message each time a message arrives.
Generates and throws a <code>CustomErrorMessage</code> each time a message arrives. The text of the error message is dynamically created using a SpEL expression that is evaluated on the incoming message.

This can be used to trigger the error handling of the message flow with an error message that contains useful information for locating the problem. For example, when throwing a custom error message in a flow that is exposed as a web service, this custom error is send back to the caller as a <i>SOAP fault</i>.

Note that this <i>service activator</i> will never produce any output messages.

#### Expression
<i>SpEL</i> expression to be evaluated on each incoming message. The result of this evaluation will be used as the text for the custom error message.

<i>Required</i>


<i><b>Examples</b></i>

An example of a simple SpEL expression that always results in the same (static) message:
<pre>
'Oops, something went wrong!'
</pre>

An example of a more complex SpEL expression that uses header information from the input message:
<pre>
'Request for user "' + (headers['example_user'] ?: 'anonymous') + '" failed.'
</pre>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

