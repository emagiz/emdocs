---
id: xslt-extension-gateway
title: XSLT extension gateway
sidebar_label: XSLT extension gateway
---
#### Gateway that is called from extension functions in XSLT transformations.
If an XSLT transformer uses the <code>ezx:call-xslt-extension-gateway(...)</code> function, the request and response XML messages go through this gateway. This allows users to completely configure the behaviour of the function call, using the messaging components and functionality that are available for "normal" flows.

A typical usage scenario is the case where an XML message need to be transformed and enriched with data obtained from another source. For example, the XML message might contain just a customer number but needs to be enriched with full customer details which can be obtained by calling an (external) web service.

To call this gateway from an <i>XSLT transformer</i>, pass the gateway as an <i>XSLT parameter</i> to the stylesheet and use this parameter to call the <code>ezx:call-xslt-extension-gateway(...)</code> XSLT function.

To pass the gateway as an <i>XSLT parameter</i>, use the <code>@'component-id'</code> syntax for the SpEL expression that determines the value of the parameter. For example, if the <b>full</b> id of this gateway is <code>my.flow.receive.xslt-extension-gateway</code>, the SpEL expression would be <code>@'my.flow.receive.xslt-extension-gateway'</code>.

#### Request channel
Channel where request messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the request messages.

<i>Required</i>

#### Reply channel
Channel to consume the reply messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Service interface
The name of the interface which will be exposed by this gateway.

#### Request timeout
The amount of time (in milliseconds) the dispatcher would wait to send a message. This timeout would only apply if there is a potential to block in the send call, for example if this gateway is hooked up to a queue channel.

#### Reply timeout
Allows you to specify how long this gateway will wait (in milliseconds) for the reply message before returning <code>null</code>.

By default it will wait indefinitely.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this gateway's invocation.

If no <i>error channel</i> is provided (the default), this gateway will propagate exceptions to the caller.

To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.

