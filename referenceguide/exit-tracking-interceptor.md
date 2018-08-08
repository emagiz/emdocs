
Channel interceptor that sends exit tracking messages to the specified tracking channel. 
Channel interceptor that sends exit tracking messages to the specified tracking channel. 

The generated tracking messages will be complete, well-formed XML documents represented as a String. These messages will contain one &lt;exit-tracking&gt; element, as defined by the XML schema located at:
classpath:com/emagiz/components/tracking/emagiz-tracking-1.0.xsd 

The tracked message is expected to contain the TrackingHeaders.ID header, which should've been added by an upstream EntryTrackingInterceptor.


Channel
Channel to send tracking message to.

<i>Required</i>


Location
String describing the location of this interceptor.

<i>Required</i>


Timeout
The timeout when sending to the tracking channel.

A positive value indicates the maximum amount of time (in milliseconds) for waiting on a successful send when the channel is at capacity. A value of zero indicates no waiting at all if the channel is at capacity at the moment of the initial attempt. A negative value indicates waiting indefinitely for a successful send when the channel is at capacity.

Default is <code>0</code>, which indicates no waiting for a successful send to the tracking channel.


Omit headers
Whether this tracking interceptor should exclude the headers of the tracked message in the tracking message or not.

Note that the headers <code>id</code>, <code>timestamp</code>, <code>sequenceNumber</code>, <code>sequenceSize</code>, <code>history</code> and <code>emagiz_tracking_id</code> are never included in the list of tracked headers, since these values are already used elsewhere in the tracking message.

Default is <code>false</code>.


Omit payload
Whether this tracking interceptor should exclude the payload content and payload class of the tracked message in the tracking message or not. 

Note that the payload content is always converted to a string value for tracking purposes. This is achieved by first trying to convert the payload object using an <code>XmlToStringTransformer</code>, and when this fails calling <code>String.valueOf(Object)</code> on the payload. If this is undesirable because the string conversion is quite expensive or the payload is very large, omitting the payload in the tracking messages can lead to a significant performance increase. 

Default is <code>false</code>.

