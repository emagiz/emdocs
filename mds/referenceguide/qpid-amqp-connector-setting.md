# JDBC H2 connection pool
A simple standalone JDBC connection pool.

#### URL
The URL used to stablished a connection with an h2 database. A new database is automatically created.

Example: jdbc:h2:${emagiz.data}/h2/messagestore

More information related to the URL syntax can be found in the 
<a href="http://www.h2database.com/html/features.html#database_url" target="_blank">documentation</a>.




#### Username
Database username

#### Password
Database username password

#### Max connections
The maximum number of connections to use.

Default value is <code>10</code>

#### Login timeout
The maximum time in seconds to wait for a free connection.

Default value is <code>30</code>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

# Qpid AMQP connector settings
Qpid JMS client connector settings that are part of a connection factory supporting AMQP.

These setting contain host, port and optionally (WebSockets only) path for the URI used per connector. In addition, the default connection settings can be overriden per individual connector.

#### Host
This specifies the host name or IP address to connect to when configuring a connector.

The host name can be used by the JVM for the TLS SNI (Server Name Indication) extension in order to communicate the desired server hostname during a TLS handshake. The SNI extension will be automatically included if a Fully Qualified name (e.g myhost.mydomain) is specified, but not when an unqualified name (e.g myhost) or bare IP address are used.


<i>Required</i>

#### Port
This specifies the port to connect to when configuring a connector. 

<i>Required</i>

#### Path
When WebSocket is used, this allows you to specify the path part of the URI (e.g., /orderId/{order}). Should start with a / (forward slash).

<i>Optional</i>

#### Send buffer size
The send buffer size in bytes. The value must be greater than zero or an <code> IllegalArgumentException</code> will be thrown.

The default value for this property is 65536 bytes (64KiB).

#### Receive buffer size
This parameter determines the size of the TCP receive buffer in bytes. The value must be greater than zero or an <code>IllegalArgumentException</code> will be thrown.

The default value for this property is 65536 bytes (64KiB).

#### Traffic class
The traffic class value used by the TCP connection. A valid value should be between 0 and 255.


Default is 0.

#### Connection timeout
The timeout (in milliseconds) for creating connections to the specified server. 

Default is 60000 milliseconds (60 seconds).

#### Socket timeout
The socket's timeout in milliseconds on blocking socket operations.

With this option set to a non-zero timeout, a read() call on the InputStream associated with this Socket will block for only this amount of time. If the timeout expires, a <code>java.net.SocketTimeoutException </code> is raised, though the Socket is still valid. The option must be enabled prior to entering the blocking operation to have effect. The timeout must be > 0. A timeout of zero is interpreted as an infinite timeout.


Default value is -1 (disabled).

#### Socket linger
The socket's linger on close timeout value in seconds.

This option disables/enables immediate return from a close() of a TCP Socket. Enabling this option with a non-zero Integer timeout means that a close() will block pending the transmission and acknowledgement of all data written to the peer, at which point the socket is closed gracefully. Upon reaching the linger timeout, the socket is closed forcefully, with a TCP RST. Enabling the option with a timeout of zero does a forceful close immediately. If the specified timeout value exceeds 65,535 it will be reduced to 65,535.

Default is -1 (disabled).

#### TCP keep alive
Enables the TCP keep alive value to prevent connections from timing out at the TCP level.
 
For more information, see <a href="http://tldp.org/HOWTO/TCP-Keepalive-HOWTO/overview.html">Documentation</a>

Default is false.

#### TCP no delay
Default is true.

#### Use Epoll layer
When true, the transport will use the native Epoll layer when available, instead of the NIO layer, which can improve performance.

Defaults to true.

#### Use KQueue layer
When true, the transport will use the native KQueue layer when available, instead of the NIO layer, which can improve performance.

Defaults to false.

#### UI_usesSSL
Enable SSL to secure connections.

Default is false

####  Enabled cipher suites
The cipher suites to enable, comma separated. Any disabled ciphers are removed from this.

No default, meaning the context default ciphers are used.

#### Disabled cipher suites
The cipher suites to disable, comma separated. Ciphers listed here are removed from the enabled ciphers.

No default.

#### Enabled protocols
The protocols to enable, comma separated. Any disabled protocols are removed from this.

No default, meaning the context default protocols are used.

#### Disabled protocols
The protocols to disable, comma separated. Protocols listed here are removed from the enabled protocols.

Default is "SSLv2Hello,SSLv3".

#### Verify host
Whether to verify that the hostname being connected to matches with the provided server certificate.

Defaults to true.

#### Use SASL  layer
Controls whether connections should use a SASL layer or not.

Default is true.

#### SASL mechanisms
Which SASL mechanism(s) the client should allow selection of, if offered by the server and usable with the configured credentials. Comma separated if specifying more than 1 mechanism. The clients supported mechanisms are currently EXTERNAL, SCRAM-SHA-256, SCRAM-SHA-1, CRAM-MD5, PLAIN, ANONYMOUS.

Default is to allow selection from all those mechanisms.

#### Idle timeout
The idle timeout in milliseconds after which the connection will be failed if the peer sends no AMQP frames.

Default is 60000 milliseconds.

#### vhost
The vhost to connect to. Used to populate the Sasl and Open hostname fields.

Default is the main hostname from the Connection URI.

#### Max frame size
The max-frame-size value in bytes that is advertised to the peer.

Default is 1048576 bytes.

#### Drain timeout
The time in milliseconds that the client will wait for a response from the remote host when a consumer drain request is made. If no response is seen in the allotted timeout period, the link will be considered failed and the associated consumer will be closed.

Default is 60000 milliseconds.

#### Allow non-secure redirects
Controls whether an AMQP connection will allow for a redirect to an alternative host over a connection that is not secure when the existing connection is secure, e.g. redirecting an SSL connection to a raw TCP connection.

Default is false.

