---
id: global-channel-interceptor
title: Global channel interceptor
sidebar_label: Global channel interceptor
---
#### Pattern
Channel name(s) or patterns this interceptor will be added to.

To specify more than one channel use <code>','</code> (e.g., <code>pattern="input*, foo, bar"</code>).

<i>Required</i>


Channel interceptor that sends entry tracking messages to the specified tracking channel. 

The generated tracking messages will be complete, well-formed XML documents represented as a String. These messages will contain one &lt;entry-tracking&gt; element, as defined by the XML schema located at:
classpath:com/emagiz/components/tracking/emagiz-tracking-1.0.xsd 

The tracked message is slightly altered by this interceptor, because the TrackingHeaders.ID header is added to it. This header is required for the expected downstream ExitTrackingInterceptor to function.


Channel interceptor that sends exit tracking messages to the specified tracking channel. 

The generated tracking messages will be complete, well-formed XML documents represented as a String. These messages will contain one &lt;exit-tracking&gt; element, as defined by the XML schema located at:
classpath:com/emagiz/components/tracking/emagiz-tracking-1.0.xsd 

The tracked message is expected to contain the TrackingHeaders.ID header, which should've been added by an upstream EntryTrackingInterceptor.


Channel interceptor that sends debug messages to the specified debug channel.

The generated debug messages will be complete, well-formed XML documents represented as a string. These messages will contain one &lt;debug-message&gt; element, as defined by the XML schema located at:
<code>classpath:com/emagiz/components/debug/emagiz-debug-1.0.xsd</code>

The intercepted message is not altered at all by this interceptor, nor should this interceptor ever cause any exceptions to interfere with the main message flow: any exceptions that occur are simply logged as error messages.

This interceptor will start deactivated and can be activated by calling <code>activate(String, long)</code>. When not activated, no debug messages will be produced.

#### Order
Specifies the order in which this interceptor will be added to the existing channel interceptors (if any).

Negative value (e.g., <code>-2</code>) will signify <b>before</b> existing interceptors (if any).
Positive value (e.g., <code>2</code>) will signify <b>after</b> existing interceptors (if any).

<i>Optional</i>


Channel interceptor that sends entry tracking messages to the specified tracking channel. 

The generated tracking messages will be complete, well-formed XML documents represented as a String. These messages will contain one &lt;entry-tracking&gt; element, as defined by the XML schema located at:
classpath:com/emagiz/components/tracking/emagiz-tracking-1.0.xsd 

The tracked message is slightly altered by this interceptor, because the TrackingHeaders.ID header is added to it. This header is required for the expected downstream ExitTrackingInterceptor to function.


Channel interceptor that sends exit tracking messages to the specified tracking channel. 

The generated tracking messages will be complete, well-formed XML documents represented as a String. These messages will contain one &lt;exit-tracking&gt; element, as defined by the XML schema located at:
classpath:com/emagiz/components/tracking/emagiz-tracking-1.0.xsd 

The tracked message is expected to contain the TrackingHeaders.ID header, which should've been added by an upstream EntryTrackingInterceptor.


Channel interceptor that sends debug messages to the specified debug channel.

The generated debug messages will be complete, well-formed XML documents represented as a string. These messages will contain one &lt;debug-message&gt; element, as defined by the XML schema located at:
<code>classpath:com/emagiz/components/debug/emagiz-debug-1.0.xsd</code>

The intercepted message is not altered at all by this interceptor, nor should this interceptor ever cause any exceptions to interfere with the main message flow: any exceptions that occur are simply logged as error messages.

This interceptor will start deactivated and can be activated by calling <code>activate(String, long)</code>. When not activated, no debug messages will be produced.

#### Channel
Channel to send debug message to.

<i>Required</i>

#### Timeout
The timeout when sending to the debug channel.

A positive value indicates the maximum amount of time (in milliseconds) for waiting on a successful send when the channel is at capacity. A value of zero indicates no waiting at all if the channel is at capacity at the moment of the initial attempt. A negative value indicates waiting indefinitely for a successful send when the channel is at capacity.

Default is <code>0</code>, which indicates no waiting for a successful send to the debug channel.

#### Timeout
The timeout when sending to the tracking channel.

A positive value indicates the maximum amount of time (in milliseconds) for waiting on a successful send when the channel is at capacity. A value of zero indicates no waiting at all if the channel is at capacity at the moment of the initial attempt. A negative value indicates waiting indefinitely for a successful send when the channel is at capacity.

Default is <code>0</code>, which indicates no waiting for a successful send to the tracking channel.

#### Omit headers
Whether this tracking interceptor should exclude the headers of the tracked message in the tracking message or not.

Note that the headers <code>id</code>, <code>timestamp</code>, <code>sequenceNumber</code>, <code>sequenceSize</code>, <code>history</code> and <code>emagiz_tracking_id</code> are never included in the list of tracked headers, since these values are already used elsewhere in the tracking message.

Default is <code>false</code>.

#### Omit payload
Whether this tracking interceptor should exclude the payload content and payload class of the tracked message in the tracking message or not. 

Note that the payload content is always converted to a string value for tracking purposes. This is achieved by first trying to convert the payload object using an <code>XmlToStringTransformer</code>, and when this fails calling <code>String.valueOf(Object)</code> on the payload. If this is undesirable because the string conversion is quite expensive or the payload is very large, omitting the payload in the tracking messages can lead to a significant performance increase. 

Default is <code>false</code>.

#### Timeout
The timeout when sending to the tracking channel.

A positive value indicates the maximum amount of time (in milliseconds) for waiting on a successful send when the channel is at capacity. A value of zero indicates no waiting at all if the channel is at capacity at the moment of the initial attempt. A negative value indicates waiting indefinitely for a successful send when the channel is at capacity.

Default is <code>0</code>, which indicates no waiting for a successful send to the tracking channel.

#### Omit headers
Whether this tracking interceptor should exclude the headers of the tracked message in the tracking message or not.

Note that the headers <code>id</code>, <code>timestamp</code>, <code>sequenceNumber</code>, <code>sequenceSize</code>, <code>history</code> and <code>emagiz_tracking_id</code> are never included in the list of tracked headers, since these values are already used elsewhere in the tracking message.

Default is <code>false</code>.

#### Omit payload
Whether this tracking interceptor should exclude the payload content and payload class of the tracked message in the tracking message or not. 

Note that the payload content is always converted to a string value for tracking purposes. This is achieved by first trying to convert the payload object using an <code>XmlToStringTransformer</code>, and when this fails calling <code>String.valueOf(Object)</code> on the payload. If this is undesirable because the string conversion is quite expensive or the payload is very large, omitting the payload in the tracking messages can lead to a significant performance increase. 

Default is <code>false</code>.

#### Channel
Channel to send tracking message to.

<i>Required</i>

#### Location
String describing the location of this interceptor.

<i>Required</i>

#### Channel
Channel to send tracking message to.

<i>Required</i>

#### Location
String describing the location of this interceptor.

<i>Required</i>

---
id: global-channel-interceptor
title: Global channel interceptor
sidebar_label: Global channel interceptor
---
#### Pattern
Channel name(s) or patterns this interceptor will be added to.

To specify more than one channel use <code>','</code> (e.g., <code>pattern="input*, foo, bar"</code>).

<i>Required</i>


Channel interceptor that sends debug messages to the specified debug channel.

The generated debug messages will be complete, well-formed XML documents represented as a string. These messages will contain one &lt;debug-message&gt; element, as defined by the XML schema located at:
<code>classpath:com/emagiz/components/debug/emagiz-debug-1.0.xsd</code>

The intercepted message is not altered at all by this interceptor, nor should this interceptor ever cause any exceptions to interfere with the main message flow: any exceptions that occur are simply logged as error messages.

This interceptor will start deactivated and can be activated by calling <code>activate(String, long)</code>. When not activated, no debug messages will be produced.

#### Order
Specifies the order in which this interceptor will be added to the existing channel interceptors (if any).

Negative value (e.g., <code>-2</code>) will signify <b>before</b> existing interceptors (if any).
Positive value (e.g., <code>2</code>) will signify <b>after</b> existing interceptors (if any).

<i>Optional</i>


Channel interceptor that sends debug messages to the specified debug channel.

The generated debug messages will be complete, well-formed XML documents represented as a string. These messages will contain one &lt;debug-message&gt; element, as defined by the XML schema located at:
<code>classpath:com/emagiz/components/debug/emagiz-debug-1.0.xsd</code>

The intercepted message is not altered at all by this interceptor, nor should this interceptor ever cause any exceptions to interfere with the main message flow: any exceptions that occur are simply logged as error messages.

This interceptor will start deactivated and can be activated by calling <code>activate(String, long)</code>. When not activated, no debug messages will be produced.

#### Channel
Channel to send debug message to.

<i>Required</i>

#### Timeout
The timeout when sending to the debug channel.

A positive value indicates the maximum amount of time (in milliseconds) for waiting on a successful send when the channel is at capacity. A value of zero indicates no waiting at all if the channel is at capacity at the moment of the initial attempt. A negative value indicates waiting indefinitely for a successful send when the channel is at capacity.

Default is <code>0</code>, which indicates no waiting for a successful send to the debug channel.

