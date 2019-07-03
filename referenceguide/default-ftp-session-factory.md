---
id: default-ftp-session-factory
title: Default FTP session factory
sidebar_label: Default FTP session factory
---
#### Session factory for creating connections with an FTP server.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/ftp.html#ftp-session-factory" target="_blank">Documentation</a>

Simple FTP session factory that doesn't provide session caching/pooling, but creates a new session for every request.

When used by a <i>FTP inbound channel adapter</i> this creates a new session + login attempt each time the adapter synchronizes the remote FTP directory. When used by a <i>FTP outbound channel adapter</i> this creates a new session + login attempt each time the adapter receives a message.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

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

