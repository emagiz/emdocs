---
id: proxy-web-service-message-sender
title: Proxy web service message sender
sidebar_label: Proxy web service message sender
---
#### Extension of HTTP Components message sender that uses a proxy for the HTTP connection.
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/client.html#d4e1703" target="_blank">External documentation</a>

WebServiceMessageSender implementation that uses a proxy and a Apache HTTP Components HttpClient to execute POST requests. 

Allows to use a preconfigured HttpClient instance, potentially with authentication, HTTP connection pooling, etc. Authentication can also be set by injecting a Credentials instance (such as the UsernamePasswordCredentials).

#### Proxy host
Hostname (IP or DNS name) of the proxy

Can be 'empty'

#### Proxy port
The port of the proxy; '-1' indicates the default protocol port

Required.

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

---
id: proxy-web-service-message-sender
title: Proxy web service message sender
sidebar_label: Proxy web service message sender
---
#### Extension of HTTP Components message sender that uses a proxy for the HTTP connection.
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/client.html#d4e1703" target="_blank">Documentation</a>

WebServiceMessageSender implementation that uses a proxy and a Apache HTTP Components HttpClient to execute POST requests. 

Allows to use a preconfigured HttpClient instance, potentially with authentication, HTTP connection pooling, etc. Authentication can also be set by injecting a Credentials instance (such as the UsernamePasswordCredentials).

#### Proxy host
Hostname (IP or DNS name) of the proxy

Can be 'empty'

#### Proxy port
The port of the proxy; '-1' indicates the default protocol port

Required.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

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

