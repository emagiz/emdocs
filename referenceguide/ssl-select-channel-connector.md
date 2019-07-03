---
id: ssl-select-channel-connector
title: SSL select channel connector
sidebar_label: SSL select channel connector
---
#### SSL select channel connector.

Extension of the <i>select channel connector</i> that adds SSL support to the connection. Use this connector if you want to use HTTPS for the communication. Note that this requires a (valid) SSL certificate.

This connector uses efficient buffers with a non blocking threading model. Direct buffers are used and threads are only allocated to connections with requests. Synchronization is used to simulate blocking for the servlet API, and any unflushed content at the end of request handling is written asynchronously.

#### Host
The hostname representing the interface to which this connector will bind, or empty for all interfaces.

#### Port
The port to listen of for connections or <code>0</code> if any available port may be used.

The standard port for the HTTPS protocol is <code>443</code>.

<i>Required</i>

#### Key store path
Path to the Java key store containing the SSL certificate for this connector.

<i>Required</i>

#### Key store
Select the Java key store containing the SSL certificate for this connector.

<i>Required</i>

#### Key store password
Password of the Java key store containing the SSL certificate for this connector.

<i>Required</i>

#### Certificate alias
Alias of the SSL certificate for this connector.

If the key store contains multiple certificates, you can use this property to specify which certificate should be used for this connector.

<i>Optional</i>

#### Key manager password
The password for the specific key within the key store.

Usually keys use the same password (or none) as the key store and you don't need this property, but when a key has a different password you can specify it here.

<i>Optional</i>

#### Trust store path
Path to the Java trust store for this connector.

<i>Optional</i>

#### Trust store
Select the Java trust store for this connector.

<i>Optional</i>

#### Trust store password
Password of the Java trust store for this connector.

<i>Optional</i>

#### Need client auth
Set to <code>true</code> if SSL needs client authentication.

Default is <code>false</code>.

#### Want client auth
Set to <code>true</code> if SSL wants client authentication.

Default is <code>false</code>.

#### Validate certs
Set to <code>true</code> if SSL certificates have to be validated, for example checking the expiration date. Invalid certificates will cause this connector to fail during startup.

Default is <code>false</code>.

#### Validate peer certs
Set to <code>true</code> if SSL certificates of the peer have to be validated, for example checking the expiration date. Invalid peer certificates will cause the connection to be rejected.

Default is <code>false</code>.

#### Protocol
The SSL protocol to use.

Default is <i>TLS</i>.

