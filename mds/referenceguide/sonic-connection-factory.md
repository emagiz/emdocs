---
id: sonic-connection-factory
title: Sonic connection factory
sidebar_label: Sonic connection factory
---
#### A JMS ConnectionFactory used to create connections with SonicMQ.
To use this connection factory, copy the following Java libraries from your <i>Sonic MQ</i> installation location to the <code>extensions</code> directory of the eMagiz runtime:

- <code>sonic_Client.jar</code>
- <code>sonic_Crypto.jar</code>
- <code>sonic_XMessage.jar</code>

Tested with versions 7.5 and 7.6 of <i>Sonic MQ</i>; should also work with all versions that have a compatible <code>ConnectionFactory</code> interface.

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

---
id: sonic-connection-factory
title: Sonic connection factory
sidebar_label: Sonic connection factory
---
#### A JMS ConnectionFactory used to create connections with SonicMQ.
To use this connection factory, copy the following Java libraries from your <i>Sonic MQ</i> installation location to the <code>extensions</code> directory of the eMagiz runtime:

- <code>sonic_Client.jar</code>
- <code>sonic_Crypto.jar</code>
- <code>sonic_XMessage.jar</code>

Tested with versions 7.5 and 7.6 of <i>Sonic MQ</i>; should also work with all versions that have a compatible <code>ConnectionFactory</code> interface.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Fault tolerant
Enable or disable fault tolerant connection creation.

By default, connections are created non-fault tolerant(false). For a connection to be created fault-tolerant the broker must support(be licensed for) fault-tolerance.

#### Connection URLs
Comma-separated list of broker URLs. Allows a client to connect to the first available broker on a list. 

This option can be used independently of any other load balancing options.

#### Default user
Default user.

Used when no user is provided in another way.

#### Default password
Default password.

Used when no password is provided in another way.

