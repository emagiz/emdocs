
Pattern
Channel name(s) or patterns this wire tap will be added to.

To specify more than one channel use <code>','</code> (e.g., <code>pattern="input*, foo, bar"</code>).

<i>Required</i>


Order
Specifies the order in which this interceptor will be added to the existing channel interceptors (if any).

Negative value (e.g., <code>-2</code>) will signify <b>before</b> existing interceptors (if any).
Positive value (e.g., <code>2</code>) will signify <b>after</b> existing interceptors (if any).

<i>Optional</i>


Channel
The channel to put the intercepted messages on.


Selector expression
A boolean SpEL expression evaluated against the message to determine whether it should sent to the intercepting channel.

Default is <i>empty</i>, which will cause every message to be intercepted and send to the wire tap channel.


Timeout
The timeout when sending to the wire tap channel.

A positive value indicates the maximum amount of time (in milliseconds) for waiting on a successful send when the channel is at capacity. A value of zero indicates no waiting at all if the channel is at capacity at the moment of the initial attempt. A negative value indicates waiting indefinitely for a successful send when the channel is at capacity.

Default is 0, which indicates no waiting for a successful send to the wire tap channel.

