---
id: kafka-outbound-channel-adapter
title: Kafka outbound channel adapter
sidebar_label: Kafka outbound channel adapter
---

Sends messages to the kafka broker defined in the Kafka template.

<a href="https://kafka.apache.org/" target="_new">Kafka documentation</a>
<a href="https://docs.spring.io/spring-kafka/docs/1.3.9.RELEASE/reference/html/" target="_new">Spring Kafka documentation</a>
<a href="https://github.com/spring-projects/spring-integration-kafka/blob/master/README.adoc" target="_new">Spring Integration Kafka documentation</a>

### _id
Specify the Kafka template that describes the Kafka broker.

<i>Required</i>

### _id
Specify the channel to which an error message for a failed send will be sent.

### _id
Specifies the channel to which a message with record metadata will be sent after a successful send.

### _id
Specify the Kafka template that describes the Kafka broker.

<i>Required</i>

### _id
Specify the channel to which an error message for a failed send will be sent.

### _id
Specifies the channel to which a message with record metadata will be sent after a successful send.


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

---
id: kafka-outbound-channel-adapter
title: Kafka outbound channel adapter
sidebar_label: Kafka outbound channel adapter
---

Sends messages to the kafka broker defined in the Kafka template.

<a href="https://kafka.apache.org/" target="_new">Kafka documentation</a>
<a href="https://docs.spring.io/spring-kafka/docs/1.3.9.RELEASE/reference/html/" target="_new">Spring Kafka documentation</a>
<a href="https://github.com/spring-projects/spring-integration-kafka/blob/master/README.adoc" target="_new">Spring Integration Kafka documentation</a>

### _id
Specify the Kafka template that describes the Kafka broker.

<i>Required</i>

### _id
Specify the channel to which an error message for a failed send will be sent.

### _id
Specifies the channel to which a message with record metadata will be sent after a successful send.

### _id
Specify the Kafka template that describes the Kafka broker.

<i>Required</i>

### _id
Specify the channel to which an error message for a failed send will be sent.

### _id
Specifies the channel to which a message with record metadata will be sent after a successful send.


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

