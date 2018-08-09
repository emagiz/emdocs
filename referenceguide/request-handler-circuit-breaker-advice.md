
Saves time/resources by "turning off" failing endpoints for some period of time.
The general idea of the <i>circuit breaker pattern</i> is that, if a service is not currently available, then don't waste time (and resources) trying to use it. When the circuit breaker is in the <i>closed</i> state, the endpoint will attempt to invoke the service. The circuit breaker goes to the <i>open</i> state if a certain number of consecutive attempts fails; when it is in the <i>open</i> state, new requests will "fail fast" and no attempt will be made to invoke the service until some time has expired.

When that time has expired, the circuit breaker is set to the <i>half-open</i> state. When in this state, if even a single attempt fails, the breaker will immediately go to the <i>open</i> state; if the attempt succeeds, the breaker will go to the <i>closed</i> state, in which case, it won't go to the <i>open</i> state again until the configured number of consecutive failures again occur. Any successful attempt resets the state to zero failures for the purpose of determining when the breaker might go to the <i>open</i> state again.

Typically, this might be used for external services where it might take some time to fail (such as a timeout attempting to make a network connection).


Threshold
The number of consecutive failures that need to occur before the breaker goes open.

Default is <code>5</code>.


Half open after
The time after the last failure that the breaker will wait before attempting another request.

Default is <code>1000</code> milliseconds (1 second).

