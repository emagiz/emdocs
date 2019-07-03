---
id: default-ftps-session-factory
title: Default FTPS session factory
sidebar_label: Default FTPS session factory
---
#### Session factory for creating connections with an FTPS server.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/ftp.html#ftp-session-factory" target="_blank">Documentation</a>

Simple FTPS session factory that doesn't provide session caching/pooling, but creates a new session for every request.

When used by a <i>FTP inbound channel adapter</i> this creates a new session + login attempt each time the adapter synchronizes the remote FTPS directory. When used by a <i>FTP outbound channel adapter</i> this creates a new session + login attempt each time the adapter receives a message.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Protocol
The secure socket protocol to be used, e.g. <code>SSL/TLS</code>.

Default is <code>TLS</code>.

#### Implicit
The security mode:
<i>true</i>: implicit mode
<i>false</i>: explicit mode

Default is <i>false</i> (explicit mode).

#### Session creation
Controls whether a new SSL session may be established by this socket.

Default is <i>true</i>.

#### Use client mode
Configures the socket to use client (or server) mode in its first handshake.

Default is <i>true</i> (client mode).

#### Need client auth
If <i>true</i>, configures the socket to require client authentication.

Default is <i>false</i> (client authentication not required).

#### Wants client auth
Configures the socket to request client authentication, but only if such a request is appropriate to the cipher suite negotiated.

Default is <i>false</i> (don't request client authentication).

#### AUTH value
Set <code>AUTH</code> command use value. This processing is done before connected processing.

Default is <code>TLS</code>.

#### Cipher suites
Comma-separated list of cipher suites. Controls which particular cipher suites are enabled for use on this connection. Called before server negotiation.

Default is <code>null</code> (no particular cipher suites enabled).

#### PROT
Data channel protection level (<code>PROT</code> command):
<code>C</code> - Clear
<code>S</code> - Safe (SSL protocol only)
<code>E</code> - Confidential (SSL protocol only)
<code>P</code> - Private

Default is <code>P</code> (private).

#### Protocols
Comma-separated list of protocol versions. Controls which particular protocol versions are enabled for use on this connection.

Default is <code>null</code> (no particular protocols enabled).

#### File type
Indicates how the file(s) being transfered should be treated:
<code>0</code> - ASCII file type
<code>1</code> - EBCDIC file type
<code>2</code> - Binary file type
<code>3</code> - Local file type

Default is <code>2</code> (binary file type, i.e. no translations should be performed).

#### Buffer size
Default is '2048'.

see https://issues.apache.org/jira/browse/NET-207

#### Client mode
Indicates how data transfers are expected to occur between the client (local) and server (remote). Choices are:

<b><code>0</code> - Active local data connection mode</b>
The server should connect to the client's data port to initiate a data transfer. Note that these types of connections are problematic when the server is not located in the same network, because firewalls on the client side usually block incoming connections.

<b><code>2</code> - Passive local data connection mode</b>
The server is in passive mode, requiring the client to connect to the server's data port to initiate a transfer.

Default is <code>0</code> (active mode).

#### Control encoding
Sets the character encoding used by the FTP control connection. Some FTP servers require that commands be issued in a non-ASCII encoding like <code>UTF-8</code> so that filenames with multi-byte character representations (e.g, <i>Big 8</i>) can be specified.

Default is <code>ISO-8859-1</code>.

#### Connect timeout
The socket timeout (in milliseconds) when connecting to the server.

A timeout of zero is interpreted as an infinite timeout: the connection will block until established or an error occurs.

Default is <code>0</code> (infinite timeout).

#### Default timeout
The socket timeout (in milliseconds) when reading data from an established connection.

A timeout of zero is interpreted as an infinite timeout: the connection will block until the data has been read or an error occurs.

Default is <code>0</code> (infinite timeout).

#### Data timeout
The socket timeout (in milliseconds) when reading from the data connection.

A timeout of zero is interpreted as an infinite timeout: the data connection will block until the data has been read or an error occurs.

Note that this timeout will also be applied when accepting incoming connections whilst establishing an active local data connection.

Default is <code>0</code> (infinite timeout).

