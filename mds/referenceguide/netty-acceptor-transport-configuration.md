---
id: netty-acceptor-transport-configuration
title: Netty acceptor transport configuration
sidebar_label: Netty acceptor transport configuration
---
#### Netty implementation of an acceptor.
<a href="http://docs.jboss.org/hornetq/2.2.14.Final/user-manual/en/html_single/index.html#d0e3087" target="_blank">External documentation</a>

An acceptor defines a way in which connections can be made to the HornetQ server.

#### Use in-VM
If <code>true</code>, neither NIO nor OIO sockets are used, but an in-VM acceptor is created. In this case the <i>host</i> can be set to any arbitrary value that uniquely identifies a local address within the JVM, e.g. <code>"hornetq.acceptor.netty.invm"</code>. This value can then be used to connect to it, for example by using the <i>Netty tunneling request handler</i> provided in the eMagiz Mendix runtime module.

Default is <code>false</code>.

#### Use NIO
If this is 'true' then Java non blocking NIO will be used. If set to 'false' then old blocking Java IO will be used. 

If you require the server to handle many concurrent connections, we highly recommend that you use non blocking Java NIO. Java NIO does not maintain a thread per connection so can scale to many more concurrent connections than with old blocking IO. If you don't require the server to handle many concurrent connections, you might get slightly better performance by using old (blocking) IO.

The default value for this property is 'false' on the server side and 'false' on the client side.

#### Protocol
The protocol to use for this acceptor. 

<b>CORE (default)</b>
Default

<b>STOMP</b> 
Stomp is a text-orientated wire protocol that allows Stomp clients to communicate with Stomp Brokers.
<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#stomp" target="_blank">External documentation</a>

<b>STOMP_WS</b>
With this configuration, HornetQ will accept Stomp connections over Web Sockets. 
<a href="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#stomp.websockets" target="_blank">External documentation</a>

<b>AMQP </b>
AMQP support coming soon!

#### Stomp consumer credits
When consuming messages in stomp, the server will flow control the channel as messages are acknowledged. The default value is 10K. The server won't send more messages than 10K bytes until you ack more messages. 

Notice that if you use auto-ack subscriptions on stomp, you have to consume as fast as you can on your client, or you may flood the channels on Netty what will lead to OutOfMemory errors.

#### Stomp enable message ID
When receiving Stomp messages via a JMS consumer or a <code>QueueBrowser</code>, the messages have no properties like <code>JMSMessageID</code> by default. However this may bring some inconvenience to clients who wants an ID for their purpose. HornetQ Stomp provides a parameter to enable message ID on each incoming Stomp message. If you want each Stomp message to have a unique ID, just set this property to <code>true</code>. 

Default is <code>false</code>.

#### Host
This specifies the host name or IP address to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is 'localhost'.

When configuring acceptors, multiple hosts or IP addresses can be specified by separating them with commas. It is also possible to specify 0.0.0.0 to accept connection from all the host's network interfaces. It's not valid to specify multiple addresses when specifying the host for a connector; a connector makes a connection to one specific address.

#### Port
This specifies the port to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is '5445'.

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

#### Connection TTL
If you need a specific <i>connection TTL</i> for your connections without affecting the <i>connection TTL override</i> setting, you can configure your acceptor with this property, which is used to set the time-to-live for connections that are created from this acceptor.

#### Batch delay
Before writing packets to the transport, HornetQ can be configured to batch up writes for a maximum of batch-delay milliseconds. This can increase overall throughput for very small messages. It does so at the expense of an increase in average latency for message transfer.

The default value for this property is 0 ms.

#### Direct deliver
When a message arrives on the server and is delivered to waiting consumers, by default, the delivery is done on a different thread to that which the message arrived on. This gives the best overall throughput and scalability, especially on multi-core machines. However it also introduces some extra latency due to the extra context switch required. If you want the lowest latency and the possible expense of some reduction in throughput then you can make sure direct-deliver to 'true'.

The default value for this parameter is 'true'. If you are willing to take some small extra hit on latency but want the highest throughput set this parameter to 'false'.

#### NIO remoting threads
When configured to use NIO, HornetQ will, by default, use a number of threads equal to three times the number of cores (or hyper-threads) as reported by Runtime.getRuntime().availableProcessors() for processing incoming packets. If you want to override this value, you can set the number of threads by specifying this parameter.

The default value for this parameter is '-1' which means use the value from Runtime.getRuntime().availableProcessors() * 3.

#### Cluster connection
If you define more than one cluster connection, you may define what cluster connection will be used to notify topologies. This will be very useful when you are playing with multiple network interface cards (NIC) and need to isolate the cluster definitions.

The default value is the first cluster connection defined at the main configuration.

#### SSL enabled
Netty SSL is similar to the Netty TCP transport, but it provides additional security by encrypting TCP connections using the Secure Sockets Layer (SSL) / Transport Layer Security (TLS).

The encryption protocols and algorithms supported depend on the Java security provider. The default Oracle/Sun JRE SE 6 provides support for at least the following standards/protocols/algorithms: JCA, JSSE, JCE, SSL v3, TLS v1, SSL v2 Hello, RSA, AES, Blowfish, DES, Triple DES, RC2, RC4, Diffie-Hellman, DSA, X.509, PKIX, PKCS #12, MD2, MD5, SHA-1, SHA-256, SHA-384, SHA-512.

Default is <code>false</code>.

#### Need client auth
Set to <code>true</code> if SSL needs client authentication.

Default is <code>false</code>.

#### Key store path
The path to the SSL key store on the server which holds the server's certificates (whether self-signed or signed by an authority).

<i>Required</i>

#### Key store
Select the SSL key store which holds the server's certificates (whether self-signed or signed by an authority).

<i>Required</i>

#### Key store password
The password of the SSL key store which holds the server's certificates (whether self-signed or signed by an authority).

<i>Required</i>

#### Trust store path
The path to the trusted client certificate store on the server.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### Trust store
Select the trusted client certificate store.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### Trust store password 
The password of the trusted client certificate store.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

#### HTTP enabled
Netty HTTP tunnels packets over the HTTP protocol. It can be useful in scenarios where firewalls only allow HTTP traffice to pass.

Default is 'false'.

#### HTTP response time
How long the server can wait before sending an empty http response to keep the connection alive. 

Only used when HTTP is enabled. Default is '10000'.

#### HTTP server scan period
How often, in milliseconds, to scan for clients needing responses. 

Only used when HTTP is enabled. Default is '5000'.

