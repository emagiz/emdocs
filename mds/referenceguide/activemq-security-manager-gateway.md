---
id: activemq-security-manager-gateway
title: ActiveMQ security manager gateway
sidebar_label: ActiveMQ security manager gateway
---


# ActiveMQ security manager gateway
A <code>&lt;si:gateway&gt;</code> that implements the <code>ActiveMQSecurityManager</code> interface.

This gateway can be used as a custom security manager in an ActiveMQ Artemis server to handle validation of user credentials (authentication) and user roles (authorization).

Note that the <i>cluster user</i> of the ActiveMQ Artemis server always has full privileges and the validation of his credentials is done internally (never even reaching the security manager).

#### Request channel
Channel where request messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the request messages.

<i>Required</i>

#### Request channel
Channel to consume the reply messages from.

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

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

