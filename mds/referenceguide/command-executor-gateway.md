---
id: command-executor-gateway
title: Command executor gateway
sidebar_label: Command executor gateway
---
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

---
id: command-executor-gateway
title: Command executor gateway
sidebar_label: Command executor gateway
---
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

