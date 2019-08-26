---
id: request-handler-retry-advice
title: Request handler retry advice
sidebar_label: Request handler retry advice
---
#### Allows configuration of sophisticated retry scenarios when a failure occurs in the endpoint.
This advice leverages the rich retry mechanisms provided by the <i>Spring Retry</i> project.

The core component of <i>Spring Retry</i> is the <code>RetryTemplate</code>, which allows configuration of sophisticated retry scenarios, including <code>RetryPolicy</code> and <code>BackoffPolicy</code> strategies, with a number of implementations, as well as a <code>RecoveryCallback</code> strategy to determine the action to take when retries are exhausted.

#### Type
Retry policy to use for determining the number of try attempts:

<b>Simple retry policy</b>: Retries a fixed number of times. The number of attempts includes the initial try.
<b>Timout retry policy</b>: Allows a retry only if the timeout hasn't expired yet.

<i>Optional</i> ; default each operation is retried for a maximum of three attempts.

#### Max attempts
The number of attempts before a retry becomes impossible.

Default is <code>3</code>.

#### Timeout
The timeout in milliseconds.

Default is <code>1000</code> ms (1 second).

#### Type
Back off policy to use for determining the back off period between retry attempts:

<b>Fixed back off policy</b>: Pauses for a fixed period of time before continuing.
<b>Exponentional back off policy</b>: Increases the back off period for each retry attempt exponentially.
<b>Exponentional random back off policy</b>: Same as <i>exponentional back off policy</i>, but chooses a random multiple of the interval. The random multiple is selected based on how many iterations have occurred. In some cases threads might be started at the same time, and thus stomp together onto the next interval. Using this policy can help avoid that scenario.

<i>Optional</i> ; default there is no back off period between retry attempts.

#### Back off period
The back off period in milliseconds.

Default is <code>1000</code> ms (1 second).

#### Initial interval
Set the initial interval value between retry attempts in milliseconds.

Default is <code>100</code> ms.

#### Multiplier
The value used to multiply the interval period with between two retry attempts.

Default is <code>2.0</code>.

Hint: do not use values much in excess of <code>1.0</code> or the backoff will get very long very fast.

#### Max interval
The maximum interval between retry attempts. Set this to avoid infinite waits if backing off a large number of times (or if the multiplier is set too high).

Default is <code>30000</code> ms (30 seconds).

#### Initial interval
Set the initial interval value between retry attempts in milliseconds.

Default is <code>100</code> ms.

#### Multiplier
The value used to multiply the interval period with between two retry attempts.

Default is <code>2.0</code>.

Hint: do not use values much in excess of <code>1.0</code> or the backoff will get very long very fast.

#### Max interval
The maximum interval between retry attempts. Set this to avoid infinite waits if backing off a large number of times (or if the multiplier is set too high).

Default is <code>30000</code> ms (30 seconds).

#### Type
Determines how to handle the exception after the final failed retry occurs:

<b>Error message sending recoverer</b>: Sends the final exception as an <code>ErrorMessage</code> after retry exhaustion. This prevents the exception from propagating back up the message flow.

<i>Optional</i> ; default no recovery callback is specified, propagating the final exception back up the message flow (usually ending up at an upstream inbound channel adapter or gateway).

#### Error channel
The channel where the <code>ErrorMessages</code> will be send to.

<i>Required</i>

#### Send timeout
The maximum amount of time in milliseconds to wait when sending a message to the output channel.

Default is <code>-1</code>, i.e. sends will wait indefinitely.

#### Type
By default no retry state gerator is used, resulting in <i>stateless retries</i>. If you want a <i>stateful retry</i> mechanism instead, provide a retry state generator here.

<b><i>Stateless Retry</i></b>
Stateless retry is the case where the retry activity is handled entirely within the advice, where the thread pauses (if so configured) and retries the action.

<b><i>Stateful Retry</i></b>
Stateful retry is the case where the retry state is managed within the advice, but where an exception is thrown and the caller resubmits the request. An example for stateful retry is when we want the message originator (e.g. JMS) to be responsible for resubmitting, rather than performing it on the current thread. Stateful retry needs some mechanism to detect a retried submission, which is handled by the retry state generator.

#### Key expression
SpEL expression (must return a non-null object) that is evaluated on the input message to determine the key representing the state for a retry attempt, for example <code>headers.jms_messageId</code>.

Stateful retry is characterised by having to recognise the items that are being processed, so this value is used as a cache key in between failed attempts.

<i>Required</i>

#### Force refresh expression
SpEL expression (must return a boolean) that is evaluated on the input message to determine whether a cache lookup can be avoided. If the key is known ahead of the retry attempt to be fresh (i.e. has never been seen before) then a cache lookup can be avoided if this expression evaluates to <code>true</code>.

<i>Optional</i>

---
id: request-handler-retry-advice
title: Request handler retry advice
sidebar_label: Request handler retry advice
---
#### Allows configuration of sophisticated retry scenarios when a failure occurs in the endpoint.
This advice leverages the rich retry mechanisms provided by the <i>Spring Retry</i> project.

The core component of <i>Spring Retry</i> is the <code>RetryTemplate</code>, which allows configuration of sophisticated retry scenarios, including <code>RetryPolicy</code> and <code>BackoffPolicy</code> strategies, with a number of implementations, as well as a <code>RecoveryCallback</code> strategy to determine the action to take when retries are exhausted.

#### Type
Retry policy to use for determining the number of try attempts:

<b>Simple retry policy</b>: Retries a fixed number of times. The number of attempts includes the initial try.
<b>Timout retry policy</b>: Allows a retry only if the timeout hasn't expired yet.

<i>Optional</i> ; default each operation is retried for a maximum of three attempts.

#### Max attempts
The number of attempts before a retry becomes impossible.

Default is <code>3</code>.

#### Timeout
The timeout in milliseconds.

Default is <code>1000</code> ms (1 second).

#### Type
Back off policy to use for determining the back off period between retry attempts:

<b>Fixed back off policy</b>: Pauses for a fixed period of time before continuing.
<b>Exponentional back off policy</b>: Increases the back off period for each retry attempt exponentially.
<b>Exponentional random back off policy</b>: Same as <i>exponentional back off policy</i>, but chooses a random multiple of the interval. The random multiple is selected based on how many iterations have occurred. In some cases threads might be started at the same time, and thus stomp together onto the next interval. Using this policy can help avoid that scenario.

<i>Optional</i> ; default there is no back off period between retry attempts.

#### Back off period
The back off period in milliseconds.

Default is <code>1000</code> ms (1 second).

#### Initial interval
Set the initial interval value between retry attempts in milliseconds.

Default is <code>100</code> ms.

#### Multiplier
The value used to multiply the interval period with between two retry attempts.

Default is <code>2.0</code>.

Hint: do not use values much in excess of <code>1.0</code> or the backoff will get very long very fast.

#### Max interval
The maximum interval between retry attempts. Set this to avoid infinite waits if backing off a large number of times (or if the multiplier is set too high).

Default is <code>30000</code> ms (30 seconds).

#### Initial interval
Set the initial interval value between retry attempts in milliseconds.

Default is <code>100</code> ms.

#### Multiplier
The value used to multiply the interval period with between two retry attempts.

Default is <code>2.0</code>.

Hint: do not use values much in excess of <code>1.0</code> or the backoff will get very long very fast.

#### Max interval
The maximum interval between retry attempts. Set this to avoid infinite waits if backing off a large number of times (or if the multiplier is set too high).

Default is <code>30000</code> ms (30 seconds).

#### Type
Determines how to handle the exception after the final failed retry occurs:

<b>Error message sending recoverer</b>: Sends the final exception as an <code>ErrorMessage</code> after retry exhaustion. This prevents the exception from propagating back up the message flow.

<i>Optional</i> ; default no recovery callback is specified, propagating the final exception back up the message flow (usually ending up at an upstream inbound channel adapter or gateway).

#### Error channel
The channel where the <code>ErrorMessages</code> will be send to.

<i>Required</i>

#### Send timeout
The maximum amount of time in milliseconds to wait when sending a message to the output channel.

Default is <code>-1</code>, i.e. sends will wait indefinitely.

#### Type
By default no retry state gerator is used, resulting in <i>stateless retries</i>. If you want a <i>stateful retry</i> mechanism instead, provide a retry state generator here.

<b><i>Stateless Retry</i></b>
Stateless retry is the case where the retry activity is handled entirely within the advice, where the thread pauses (if so configured) and retries the action.

<b><i>Stateful Retry</i></b>
Stateful retry is the case where the retry state is managed within the advice, but where an exception is thrown and the caller resubmits the request. An example for stateful retry is when we want the message originator (e.g. JMS) to be responsible for resubmitting, rather than performing it on the current thread. Stateful retry needs some mechanism to detect a retried submission, which is handled by the retry state generator.

#### Key expression
SpEL expression (must return a non-null object) that is evaluated on the input message to determine the key representing the state for a retry attempt, for example <code>headers.jms_messageId</code>.

Stateful retry is characterised by having to recognise the items that are being processed, so this value is used as a cache key in between failed attempts.

<i>Required</i>

#### Force refresh expression
SpEL expression (must return a boolean) that is evaluated on the input message to determine whether a cache lookup can be avoided. If the key is known ahead of the retry attempt to be fresh (i.e. has never been seen before) then a cache lookup can be avoided if this expression evaluates to <code>true</code>.

<i>Optional</i>

