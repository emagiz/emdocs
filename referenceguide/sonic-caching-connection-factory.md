---
id: sonic-caching-connection-factory
title: Sonic caching connection factory
sidebar_label: Sonic caching connection factory
---
#### A JMS ConnectionFactory used to create cached (non-XA) connections with SonicMQ.
To use this connection factory, copy the following Java libraries from your <i>Sonic MQ</i> installation location to the <code>extensions</code> directory of the eMagiz runtime:

- <code>sonic_Client.jar</code>
- <code>sonic_Crypto.jar</code>
- <code>sonic_XMessage.jar</code>

Tested with versions 7.5 and 7.6 of <i>Sonic MQ</i>; should also work with all versions that have a compatible <code>ConnectionFactory</code> interface.

#### Session cache size
Specify the desired size for the JMS session cache (per JMS session type).

This cache size is the maximum limit for the number of cached sessions per session acknowledgement type (auto, client, dups_ok, transacted). As a consequence, the actual number of cached sessions may be up to four times as high as the specified value - in the unlikely case of mixing and matching different acknowledgement types.

Default is <code>1</code>: caching a single session, (re-)creating further ones on demand. Specify a number like <code>10</code> if you'd like to raise the number of cached sessions; that said, <code>1</code> may be sufficient for low-concurrency scenarios.

#### Cache producers
Whether to cache JMS message producers per JMS session instance (more specifically: one message producer per destination and session), or not cache message producers at all.

Default is <code>true</code>. Switch this to <code>false</code> in order to always recreate message producers on demand.

#### Cache consumers
Whether to cache JMS message consumers per JMS session instance (more specifically: one message consumer per destination, selector string and session), or not cache message consumers at all.

Note that durable subscribers will only be cached until logical closing of the session handle.

Default is <code>true</code>. Switch this to <code>false</code> in order to always recreate message consumers on demand.

<b>Important performance consideration</b>
When this connection factory is used by a <i>JMS outbound gateway</i> with an explicit <i>reply destination</i> configured, the gateway uses a message selector that expects a <code>JMSCorrelationID</code> to match the outbound request's <code>JMSMessageID</code>. If this property is set to <code>true</code>, that can lead to an <code>OutOfMemoryException</code> since each consumer's cache key is unique (basically the destination + the message selector). Obviously, that also means we are not benefiting from the potential performance benefits of caching message consumer instances either (rather than creating with each request/reply operation). So in these cases, either set this property to <code>false</code>, or use a <i>reply listener</i> on the gateway.

#### Client ID
Specify a JMS client ID for the single connection created and exposed by this connection factory.

Note that client IDs need to be unique among all active connections of the underlying JMS provider. Furthermore, a client ID can only be assigned if the original connection factory hasn't already assigned one.

<i>Optional</i>

#### Reconnect on exception
Specify whether the single connection should be reset (to be subsequently renewed) when a JMS exception is reported by the underlying connection.

Default is <code>true</code>, which will automatically trigger recovery based on your JMS provider's exception notifications.

Internally, this will lead to a special JMS exception listener (this connection factory itself) being registered with the underlying connection. This can also be combined with a user-specified exception listener, if desired.

#### Reconnect on failover
Whether connection failure exceptions that are successfully failed over (recognizable by error code <code>FAILOVER</code>) should cause the connection to reconnect.

In case of HornetQ, the exception listener is always called on event of connection failure, irrespective of whether the connection was successfully failed over, reconnected or reattached. The error code <code>FAILOVER</code> in such cases indicates that failover was successful, and that we still have a working connection.

Default is <code>false</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Connection URLs
Comma-separated list of broker URLs. Allows a client to connect to the first available broker on a list. 

This option can be used independently of any other load balancing options.

#### Default user
Default user.

Used when no user is provided in another way.

#### Default password
Default password.

Used when no password is provided in another way.

#### Fault tolerant
Enable or disable fault tolerant connection creation.

By default, connections are created non-fault tolerant(false). For a connection to be created fault-tolerant the broker must support(be licensed for) fault-tolerance.

