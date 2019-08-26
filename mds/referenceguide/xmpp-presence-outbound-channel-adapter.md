---
id: xmpp-presence-outbound-channel-adapter
title: XMPP presence outbound channel adapter
sidebar_label: XMPP presence outbound channel adapter
---
#### Endpoint that will publish an updated presence state on a XMPP connection.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/xmpp.html#xmpp-roster-outbound-channel-adapter" target="_blank">External documentation</a>

Configures an endpoint that will publish an updated presence state on your XMPP connection object.

#### Channel
Channel to consume messages from.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: xmpp-presence-outbound-channel-adapter
title: XMPP presence outbound channel adapter
sidebar_label: XMPP presence outbound channel adapter
---
#### Endpoint that will publish an updated presence state on a XMPP connection.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xmpp.html#xmpp-roster-outbound-channel-adapter" target="_blank">Documentation</a>

Configures an endpoint that will publish an updated presence state on your XMPP connection object.

#### Channel
Channel to consume messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

