---
id: tcp-outbound-gateway
title: TCP outbound gateway
sidebar_label: TCP outbound gateway
---
#### Used to send TCP/IP byte-messages and receive reply messages.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/ip.html#tcp-gateways" target="_blank">Documentation</a>


#### Connection factory
A <i>TCP connection factory</i> is needed by an outbound gateway. The connection factory must be of <i>client</i>.

#### Request timeout
When using a shared socket, specifies the time (in milliseconds) the gateway will wait to get access to the socket to send the request.

Default is <code>10000</code> (10 seconds).

#### Remote timeout
Specifies the time (in milliseconds) the gateway will wait for a reply from the remote system.

Default is <code>10000</code> (10 seconds).

#### Remote timeout expression
Specifies an expresssion that is evaluated against the outbound message to determine the time the gateway will wait for a reply from the remote system. Mutually exclusive with <i>remote timeout</i>.

#### Reply timeout
Allows you to specify how long (in milliseconds) this gateway will wait for the reply message to be sent successfully to the reply channel before throwing an exception. This attribute only applies when the channel might block, for example when using a bounded queue channel that is currently full.

Also, keep in mind that when sending to a <i>direct channel</i>, the invocation will occur in the sender's thread. Therefore, the failing of the send operation may be caused by other components further downstream.

If not specified, by default the gateway will wait indefinitely.

#### Request channel
Channel to consume the request messages from.

<i>Required</i>

#### Reply channel
Channel where reply messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the reply messages.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

