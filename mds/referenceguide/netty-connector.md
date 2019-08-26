---
id: netty-connector
title: Netty connector
sidebar_label: Netty connector
---


# Netty connector
<a href="https://activemq.apache.org/artemis/docs/latest/configuring-transports.html">External documentation</a>


Netty Native Transport support exists for selected OS platforms. This allows Apache ActiveMQ Artemis to use native sockets/io instead of Java NIO.

These Native transports add features specific to a particular platform, generate less garbage, and generally improve performance when compared to Java NIO based transport.

Both Clients and Server can benefit from this.

Current Supported Platforms:
- Linux running 64bit JVM
- MacOS running 64bit JVM
- Apache ActiveMQ Artemis will by default enable the corresponding native transport if a supported platform is detected.

If running on an unsupported platform or any issues loading native libs, Apache ActiveMQ Artemis will fallback onto Java NIO.

#### Use NIO
If this is <i>Yes</i> then Java non blocking NIO will be used. If set to <i>No</i> then old blocking Java IO will be used. 

If you require the server to handle many concurrent connections, we highly recommend that you use non blocking Java NIO. Java NIO does not maintain a thread per connection so can scale to many more concurrent connections than with old blocking IO. If you don't require the server to handle many concurrent connections, you might get slightly better performance by using old (blocking) IO.

The default value for this property is <i>No</i> on the server side and <i>No</i> on the client side.

#### Host
This specifies the host name or IP address to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is <code>localhost</code>.

When configuring acceptors, multiple hosts or IP addresses can be specified by separating them with commas. It is also possible to specify <code>0.0.0.0</code> to accept connection from all the host's network interfaces. It's not valid to specify multiple addresses when specifying the host for a connector; a connector makes a connection to one specific address.

#### Port
This specifies the port to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is <code>5445</code>.

#### Connect timeout
Timeout (in milliseconds) for creating connections to the specified server. 

Default is <code>-1</code> (no timeout).

#### Local address
It is possible to specify which local address the client will use when connecting to the remote address. This is typically used to control which address is used for outbound connections.

If the local address is not set then the connector will use any local address available.

#### Local port
It is possible to specify which local port the client will use when connecting to the remote address. This is typically used to control which port is used for outbound connections.

If the local port is not set, then the connector will let the system pick up an ephemeral port.

Valid ports are 0 to 65535.

#### TCP no delay
If this is <i>Yes</i> then Nagle's algorithm will be enabled.

The default value for this property is <i>Yes</i>.

#### TCP send buffer size
This parameter determines the size of the TCP send buffer in bytes.

The default value for this property is <code>32768</code> bytes (32KiB). 

TCP buffer sizes should be tuned according to the bandwidth and latency of your network. Here's a good <a href="http://www-didc.lbl.gov/TCP-tuning/"> link</a> that explains the theory behind this. In summary TCP send/receive buffer sizes should be calculated as: buffer_size = bandwidth * RTT. Where bandwidth is in bytes per second and network round trip time (RTT) is in seconds. RTT can be easily measured using the ping utility. For fast networks you may want to increase the buffer sizes from the defaults.

#### TCP receive buffer size
This parameter determines the size of the TCP receive buffer in bytes.

The default value for this property is <code>32768</code> bytes (32KiB).

#### Batch delay
Before writing packets to the transport, Artemis can be configured to batch up writes for a maximum of batch-delay milliseconds. This can increase overall throughput for very small messages. It does so at the expense of an increase in average latency for message transfer.

The default value for this property is <code>0</code> ms.

#### Remoting threads
Apache ActiveMQ Artemis will, by default, use a number of threads equal to three times the number of cores (or hyper-threads) as reported by Runtime.getRuntime().availableProcessors() for processing incoming packets. If you want to override this value, you can set the number of threads by specifying this parameter. The default value for this parameter is <code>-1</code> which means use the value from <code>Runtime.getRuntime().availableProcessors() * 3</code>.

#### SSL enabled
Netty SSL is similar to the Netty TCP transport, but it provides additional security by encrypting TCP connections using the Secure Sockets Layer (SSL) / Transport Layer Security (TLS).

The encryption protocols and algorithms supported depend on the Java security provider. The default Oracle/Sun JRE SE 6 provides support for at least the following standards/protocols/algorithms: JCA, JSSE, JCE, SSL v3, TLS v1, SSL v2 Hello, RSA, AES, Blowfish, DES, Triple DES, RC2, RC4, Diffie-Hellman, DSA, X.509, PKIX, PKCS #12, MD2, MD5, SHA-1, SHA-256, SHA-384, SHA-512.

Default is <i>No</i>

#### Keystore path
The path to the SSL key store on the client which holds the client certificates.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### Keystore password
The password of the client certificate key store.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### Truststore path
The path to the trusted server certificate store on the client.

If the server uses a self-signed certificate, you'll need to create a trust store containing this certificate. If the server uses a certificate signed by an official authority, it will most likely work without specifying a trust store because the default Java truststore already contains the recognized Certificate Authorities.

#### Truststore password
The password of the trusted server certificate store.

#### HTTP enabled
Netty HTTP tunnels packets over the HTTP protocol. It can be useful in scenarios where firewalls only allow HTTP traffice to pass.

Default is <i>No</i>.

#### HTTP client idle time
How long a client can be idle before sending an empty http request to keep the connection alive. 

Default is <code>500</code>.

#### HTTP client idle scan period
How often, in milliseconds, to scan for idle clients. 

Default is <code>500</code>.

#### HTTP requires session id
If 'true' the client will wait after the first call to receive a session id. Use when the http connector is connecting to servlet acceptor (not recommended). 

Default is <i>No</i>

#### Use servlet
The servlet transport allows Artemis traffic to be tunneled over HTTP to a servlet running in a servlet engine which then redirects it to an in-VM Artemis server.

The servlet transport differs from the Netty HTTP transport in that, with the HTTP transport HornetQ effectively acts a web server listening for HTTP traffic on, e.g. port 80 or 8080, whereas with the servlet transport Artemis traffic is proxied through a servlet engine which may already be serving web site or other applications. This allows Artemis to be used where corporate policies may only allow a single web server listening on an HTTP port, and this needs to serve all applications including messaging.

Default is <i>No</i>

#### Servlet path
The servlet path. 

#### Use global worker pool
This parameter will ensure all JMS connections share a single pool of Java threads, rather than each connection having its own pool. This serves to avoid exhausting the maximum number of processes on the operating system. 

Default is <i>Yes</i>




#### Write buffer low water mark
This parameter determines the low water mark of the Netty write buffer. Once the number of bytes queued in the write buffer exceeded the high water mark and then dropped down below this value, Netty's channel will start to be writable again. The default value for this property is <code>32768</code> bytes (32KiB).

#### Write buffer high water mark
This parameter determines the high water mark of the Netty write buffer. If the number of bytes queued in the write buffer exceeds this value, Netty's channel will start to be not writable. The default value for this property is <code>131072<code> bytes (128KiB).

#### Use epoll
Enables the use of epoll if a supported linux platform is running a 64bit JVM is detected. Setting this to <i>No</i> will force the use of Java NIO instead of epoll. Default is <i>Yes</i>.

<a href="https://en.wikipedia.org/wiki/Epoll">External documentation</a>

#### Use kqueue
Enables the use of kqueue if a supported MacOS platform running a 64bit JVM is detected. Setting this to <i>No</i> will force the use of Java NIO instead of kqueue. Default is<i>Yes</i>

<a href="https://en.wikipedia.org/wiki/Kqueue">External documentation</a>

#### Keystore provider
If not provided the default is <code>JKS</code>, based on the constant value: <code>DEFAULT_KEYSTORE_PROVIDER</code>

#### Truststore provider
If not provided the default is <code>JKS</code> based on value of the constant: <code>DEFAULT_TRUSTSTORE_PROVIDER</code>

#### Enabled cipher suites
Whether used on an acceptor or connector this is a comma separated list of cipher suites used for SSL communication. The default value is null which means the JVM's default will be used.

#### Enabled protocols
Whether used on an acceptor or connector this is a comma separated list of protocols used for SSL communication. The default value is null which means the JVM's default will be used.

Default enabled cipher suites is null.

#### Verify host
When used on an acceptor the CN of the connecting client's SSL certificate will be compared to its hostname to verify they match. This is useful only for 2-way SSL.

When used on a connector the CN of the server's SSL certificate will be compared to its hostname to verify they match. This is useful for both 1-way and 2-way SSL.

Default is <i>No</i>.

#### Use default SSL context
Only valid on a connector. Allows the connector to use the <i>default</i> SSL context (via <code>SSLContext.getDefault()</code>) which can be set programmatically by the client (via <code>SSLContext.setDefault(SSLContext)</code>). If set to <i>Yes</i> all other SSL related parameters except for sslEnabled are ignored.

Default is <i>No</i>.

#### HTTP upgrade enabled
Whether to use the <i>HTTP/1.1 Upgrade header</i> on HTTP connections. In certain situations this might be required, depending on how the incoming HTTP traffic is handled by (for example) your HTTP proxy server.

Default is <i>No</i>.

#### Trust all
When used on a connector the client will trust the provided server certificate implicitly, regardless of any configured trust store. 

Warning: This setting is primarily for testing purposes only and should not be used in production.

#### Handshake timeout
Prevents an unauthorised client opening a large number of connections and just keeping them open. As connections each require a file handle this consumes resources that are then unavailable to other clients. Once the connection is authenticated, the usual rules can be enforced regarding resource consumption. 

Default value for this property is set to <code>10</code> seconds. 

Each integer is valid value. When set value to zero or negative integer this feature is turned off. Changing value needs to restart server to take effect.

#### ActiveMQ server name
Name of the Artemis server that is passed to the HTTP request to initate the Upgrade so that the HTTP endpoint on the app server can find the
correct ActiveMQ broker that must handle the upgrade

This property is useful for colocated backups

#### CRL path
Path where the Certificate Revocation List (CRL) is located. A  CRL is a list of certificate serial numbers which have been revoked, are no longer valid, and should not be relied upon by any system user.

Default value for this property is <code>null</code>

#### SSL provider
Used to change the SSL Provider between <code>JDK</code> and <code>OPENSSL</code>. The default value for this property is <code>JDK</code>. 

If used with OPENSSL you can add netty-tcnative to your classpath to use the native installed openssl. This can be useful if you want to use special ciphersuite - elliptic curve combinations which are support through openssl but not through the JDK provider. 

For more information, see <a href="https://en.wikipedia.org/wiki/Comparison_of_TLS_implementations">External documentation</a>



#### SNI host
Overwrites the specified <i>host name</i> value at the moment of host verification.

#### Name
Name of this connector.

---
id: netty-connector
title: Netty connector
sidebar_label: Netty connector
---

<a href="https://activemq.apache.org/artemis/docs/latest/configuring-transports.html">Documentation</a>


Netty Native Transport support exists for selected OS platforms. This allows Apache ActiveMQ Artemis to use native sockets/io instead of Java NIO.

These Native transports add features specific to a particular platform, generate less garbage, and generally improve performance when compared to Java NIO based transport.

Both Clients and Server can benefit from this.

Current Supported Platforms:
- Linux running 64bit JVM
- MacOS running 64bit JVM
- Apache ActiveMQ Artemis will by default enable the corresponding native transport if a supported platform is detected.

If running on an unsupported platform or any issues loading native libs, Apache ActiveMQ Artemis will fallback onto Java NIO.

