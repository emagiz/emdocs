---
id: tcp-outbound-channel-adapter
title: TCP outbound channel adapter
sidebar_label: TCP outbound channel adapter
---
#### An outbound channel adapter that sends TCP/IP byte-messages.
<a href="http://static.springsource.org/spring-integration/docs/2.1.x/reference/html/ip.html#tcp-adapters" target="_blank">External documentation</a>


#### Connection factory
A <i>TCP connection factory</i> is needed by an outbound adapter.

If the connection factory has a type <i>client</i>, the factory is 'owned' by this adapter. 

If it has a type <i>server</i>, it is 'owned' by an inbound channel adapter and this adapter will attempt to correlate messages to the connection on which an original inbound message was received.

#### Client mode
If set to <i>true</i>, causes the adapter to establish a connection when started, rather than when the first message is sent.
 Requires a "client" connection factory, with <i>single-use</i> set to <i>false</i>.


Default is <i>false</i>.

#### Retry interval
When in client mode, specifies the retry interval (in milliseconds) if a connection
 cannot be established.

Default is <code>60000</code> (1 minute).

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

