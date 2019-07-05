---
id: connector-transport-configuration
title: Connector transport configuration
sidebar_label: Connector transport configuration
---
#### Connectors are used by a client to define how it connects to a server.
<a href="http://docs.spring.io/spring/docs/3.1.x/spring-framework-reference/html/" target="_blank">Documentation</a>


#### Name
Name of this connector.


#### Type
Connectors are used by a client to define how it connects to a server.

<b>In-VM </b> Connects to a server inside this configuration
<b>Netty </b> Connect to a server outside this configuration 

Required.


Connect to a server inside of this configuration


<a href="http://docs.jboss.org/hornetq/2.2.14.Final/user-manual/en/html_single/index.html#d0e3087" target="_blank">Documentation</a>

Netty is a high performance low level network library.

#### Server ID
Sets the server ID. 

Default is '0'.

#### Use NIO
If this is 'true' then Java non blocking NIO will be used. If set to 'false' then old blocking Java IO will be used. 

If you require the server to handle many concurrent connections, we highly recommend that you use non blocking Java NIO. Java NIO does not maintain a thread per connection so can scale to many more concurrent connections than with old blocking IO. If you don't require the server to handle many concurrent connections, you might get slightly better performance by using old (blocking) IO.

The default value for this property is 'false' on the server side and 'false' on the client side.

#### Host
This specifies the host name or IP address to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is 'localhost'.

When configuring acceptors, multiple hosts or IP addresses can be specified by separating them with commas. It is also possible to specify 0.0.0.0 to accept connection from all the host's network interfaces. It's not valid to specify multiple addresses when specifying the host for a connector; a connector makes a connection to one specific address.

#### Port
This specifies the port to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is '5445'.

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
If this is true then Nagle's algorithm will be enabled.

The default value for this property is 'true'.

#### TCP send buffer size
This parameter determines the size of the TCP send buffer in bytes.

The default value for this property is 32768 bytes (32KiB). 

TCP buffer sizes should be tuned according to the bandwidth and latency of your network. Here's a good link that explains the theory behind this: http://www-didc.lbl.gov/TCP-tuning/. In summary TCP send/receive buffer sizes should be calculated as: buffer_size = bandwidth * RTT. Where bandwidth is in bytes per second and network round trip time (RTT) is in seconds. RTT can be easily measured using the ping utility. For fast networks you may want to increase the buffer sizes from the defaults.

#### TCP receive buffer size
This parameter determines the size of the TCP receive buffer in bytes.

The default value for this property is 32768 bytes (32KiB).

#### Batch delay
Before writing packets to the transport, HornetQ can be configured to batch up writes for a maximum of batch-delay milliseconds. This can increase overall throughput for very small messages. It does so at the expense of an increase in average latency for message transfer.

The default value for this property is 0 ms.

#### NIO remoting threads
When configured to use NIO, HornetQ will, by default, use a number of threads equal to three times the number of cores (or hyper-threads) as reported by Runtime.getRuntime().availableProcessors() for processing incoming packets. If you want to override this value, you can set the number of threads by specifying this parameter.

The default value for this parameter is '-1' which means use the value from Runtime.getRuntime().availableProcessors() * 3.

#### Use NIO global worker pool
Whether a global pool should be used for the NIO worker threads or not.

Default is <code>false</code>.

#### SSL enabled
Netty SSL is similar to the Netty TCP transport, but it provides additional security by encrypting TCP connections using the Secure Sockets Layer (SSL) / Transport Layer Security (TLS).

The encryption protocols and algorithms supported depend on the Java security provider. The default Oracle/Sun JRE SE 6 provides support for at least the following standards/protocols/algorithms: JCA, JSSE, JCE, SSL v3, TLS v1, SSL v2 Hello, RSA, AES, Blowfish, DES, Triple DES, RC2, RC4, Diffie-Hellman, DSA, X.509, PKIX, PKCS #12, MD2, MD5, SHA-1, SHA-256, SHA-384, SHA-512.

Default is <code>false</code>.

#### Key store path
The path to the SSL key store on the client which holds the client certificates.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### Key store
Select the SSL key store which holds the client certificates.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### Key store password
The password of the client certificate key store.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### Trust store path
The path to the trusted server certificate store on the client.

If the server uses a self-signed certificate, you'll need to create a trust store containing this certificate. If the server uses a certificate signed by an official authority, it will most likely work without specifying a trust store because the default Java truststore already contains the recognized Certificate Authorities.

#### Trust store
Select the trusted server certificate store.

If the server uses a self-signed certificate, you'll need to create a trust store containing this certificate. If the server uses a certificate signed by an official authority, it will most likely work without specifying a trust store because the default Java truststore already contains the recognized Certificate Authorities.

#### Trust store password
The password of the trusted server certificate store.

#### HTTP enabled
Netty HTTP tunnels packets over the HTTP protocol. It can be useful in scenarios where firewalls only allow HTTP traffice to pass.

Default is 'false'.

#### HTTP client idle time
How long a client can be idle before sending an empty http request to keep the connection alive. 

Default is '500'.

#### HTTP client idle scan period
How often, in milliseconds, to scan for idle clients. 

Default is '500'.

#### HTTP requires session ID
If 'true' the client will wait after the first call to receive a session id. Use when the http connector is connecting to servlet acceptor (not recommended). 

Default is 'false'.

#### Use servlet
The servlet transport allows HornetQ traffic to be tunneled over HTTP to a servlet running in a servlet engine which then redirects it to an in-VM HornetQ server.

The servlet transport differs from the Netty HTTP transport in that, with the HTTP transport HornetQ effectively acts a web server listening for HTTP traffic on, e.g. port 80 or 8080, whereas with the servlet transport HornetQ traffic is proxied through a servlet engine which may already be serving web site or other applications. This allows HornetQ to be used where corporate policies may only allow a single web server listening on an HTTP port, and this needs to serve all applications including messaging.

Default is 'false'.

#### Servlet path
The servlet path. 

Default is '/messaging/HornetQServlet'.

