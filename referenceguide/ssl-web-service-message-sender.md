---
id: ssl-web-service-message-sender
title: SSL web service message sender
sidebar_label: SSL web service message sender
---
#### Extension of HTTP Components message sender that allows custom SSL settings.
Extension of <i>HTTP Components message sender</i> that allows custom SSL settings.

Useful when you want full control over the SSL settings for the HTTP connection, or when you need to combine functionality from the <i>HTTP Components message sender</i> (such as HTTP authentication) with SSL.

#### Trust store path
Path to the Java trust store for this HTTPS connection. Only connections to servers with a trusted certificate are allowed.

<i>Required</i>

#### Trust store
Select the path to the Java trust store for this HTTPS connection. Only connections to servers with a trusted certificate are allowed.

<i>Required</i>

#### Trust store password
Password of the Java trust store for this HTTPS connection.

<i>Required</i>

#### Key store path
Path to the Java key store containing the (client) SSL certificate(s) for this HTTPS connection. If no SSL client authentication is required, use an empty key store.

<i>Required</i>

#### Key store
Select the path to the Java key store containing the (client) SSL certificate(s) for this HTTPS connection. If no SSL client authentication is required, use an empty key store.

<i>Required</i>

#### Key store password
Password of the Java key store containing the (client) SSL certificate(s) for this HTTPS connection.

<i>Required</i>

#### Hostname verifier
Determines how to verify if a hostname matches the names stored inside the server's certificate.

<b>Allow all</b> - Allows all hostnames: essentially turns hostname verification off.
<b>Browser compatible</b> - Works the same way as Curl and Firefox: the hostname must match either the first CN, or any of the subject-alts. A wildcard can occur in the CN, and in any of the subject-alts.
<b>Strict</b> - Works the same way as Sun Java 1.4, Sun Java 5, Sun Java 6-rc. It's also pretty close to IE6. This implementation appears to be compliant with RFC 2818 for dealing with wildcards. The hostname must match either the first CN, or any of the subject-alts. A wildcard can occur in the CN, and in any of the subject-alts. The one divergence from IE6 is how we only check the first CN; IE6 allows a match against any of the CNs present.

The only difference between <i>browser compatible</i> and <i>strict</i> is that a wildcard (such as <code>*.example.com</code>) with <i>browser compatible</i> matches all subdomains (including <code>www.host.example.com</code>), while with <i>strict</i> it matches only subdomains in the same level (for example <code>www.example.com</code>).

Default is <i>browser compatible</i>.

#### Certificate alias
Alias of the SSL certificate for this HTTPS connection.

If the key store contains multiple certificates, you can use this property to specify which certificate should be used for this HTTPS connection.

<i>Optional</i>

#### Key manager password
The password for the specific key within the key store.

Usually keys use the same password (or none) as the key store and you don't need this property, but when a key has a different password you can specify it here.

<i>Optional</i>

#### Validate certs
Set to <code>true</code> if (client) SSL certificates have to be validated, for example checking the expiration date. Invalid certificates (or no certificates in the key store at all) will cause this component to fail during startup.

Default is <code>false</code>.

#### Validate peer certs
Set to <code>true</code> if SSL certificates of the peer have to be validated, for example checking the expiration date. Invalid peer certificates will cause the connection to be rejected.

Default is <code>false</code>.

#### Protocol
The SSL protocol to use.

Default is <i>TLS</i>.

#### Connection timeout
The timeout (in milliseconds) until a connection is etablished. A value of <code>0</code> means never timeout.

Default is <code>60000</code> (1 minute).

#### Read timeout
The socket read timeout (in milliseconds) for the underlying <i>HttpClient</i>. A value of <code>0</code> means never timeout.

Default is <code>60000</code> (1 minute).

#### Max total connections
The maximum number of connections allowed for the underlying <i>HttpClient</i>.

#### Auth scope
The authentication scope to be used. Only used when the credentials property has been set. 

Default is <code>ANY</code>.

#### Credentials
The credentials to be used. If not set, no authentication is done.

<b>Username password credentials</b> - Simple Credentials implementation based on a user name / password pair.
<b>NT credentials</b> - Credentials implementation for Microsoft Windows platforms that includes Windows specific attributes such as name of the domain the user belongs to.

#### Username
The user name.

This should <i>not</i> include the domain to authenticate with. For example: <code>user</code> is correct whereas <code>DOMAIN\\user</code> is not.

<i>Required</i>

#### Password
The password.

<i>Required</i>

#### Workstation
The workstation the authentication request is originating from. Essentially, the computer name for this machine.

<i>Optional</i>

#### Domain
The domain to authenticate within.

Note that this information should <i>not</i> be included in the username. For example: <code>user</code> is correct whereas <code>DOMAIN\\user</code> is not.

<i>Optional</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

