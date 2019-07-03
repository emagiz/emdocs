---
id: default-ftp-caching-session-factory
title: Default FTP caching session factory
sidebar_label: Default FTP caching session factory
---
#### Session factory for creating connections with an FTP server that uses session caching.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/ftp.html#ftp-session-caching" target="_blank">Documentation</a>

FTP session factory that provides session caching/pooling, re-using existing sessions for multiple request.

When used by a <i>FTP inbound channel adapter</i> this only creates a new session + login attempt each time the adapter synchronizes the remote FTP directory and no idle cached session is available. When used by a <i>FTP outbound channel adapter</i> this only creates a new session + login attempt each time the adapter receives a message and no idle cached session is available.

#### Session cache size
Controls how many active sessions this adapter will maintain in its cache. If the <i>session cache size</i> threshold has been reached, any attempt to acquire another session will block until either one of the cached sessions becomes available or until the wait time for a session expires.

Default is unbounded (i.e. an unlimited amount of active sessions is allowed).

#### Session wait timeout
The limit of how long to wait (in milliseconds) for a session to become available.

Default is <code>Integer.MAX_VALUE</code> (i.e. wait indefinitely for a session to become available).

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

