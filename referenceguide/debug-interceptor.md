---
id: debug-interceptor
title: Debug interceptor
sidebar_label: Debug interceptor
---
#### Channel interceptor that sends debug messages to the specified debug channel when activated.
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

