Netty acceptor
An acceptor defines a way in which connections can be made to the Artemis server.

<a href="https://activemq.apache.org/artemis/docs/latest/configuring-transports.html">Documentation</a>



Netty Native Transport support exists for selected OS platforms. This allows Apache ActiveMQ Artemis to use native sockets/io instead of Java NIO.

These Native transports add features specific to a particular platform, generate less garbage, and generally improve performance when compared to Java NIO based transport.

Both Clients and Server can benefit from this.

Current Supported Platforms:
- Linux running 64bit JVM
- MacOS running 64bit JVM
- Apache ActiveMQ Artemis will by default enable the corresponding native transport if a supported platform is detected.

If running on an unsupported platform or any issues loading native libs, Apache ActiveMQ Artemis will fallback onto Java NIO.


Normally, if the broker receives a message sent to a particular address, that has both anycast and multicast routing types enable, it will route a copy of the message to <i>one</i> of the anycast queues and to <i>all</i> of the multicast queues.

However, clients can specify a special prefix when connecting to an address to indicate which kind of routing type to use

The prefixes are custom values that are designated using the <i>anycastPrefix</i> and <i>multicastPrefix</i>.

Use in-VM
If <i>Yes</i>, neither NIO nor OIO sockets are used, but an in-VM acceptor is created. In this case the <i>host</i> can be set to any arbitrary value that uniquely identifies a local address within the JVM, e.g. <code>"artemis.acceptor.netty.invm"</code>. This value can then be used to connect to it, for example by using the <i>Netty tunneling request handler</i> provided in the eMagiz Mendix runtime module.

Use NIO
If this is <i>Yes</i> then Java non blocking NIO will be used. If set to <i>No</i> then old blocking Java IO will be used. 

If you require the server to handle many concurrent connections, we highly recommend that you use non blocking Java NIO. Java NIO does not maintain a thread per connection so can scale to many more concurrent connections than with old blocking IO. If you don't require the server to handle many concurrent connections, you might get slightly better performance by using old (blocking) IO.

The default value for this property is <i>No</i> on the server side and <i>No</i> on the client side.

Protocols
Comma separated list of supported protocol(s) by this acceptor.

<b>CORE</b>
ActiveMQ Artemis' own highly performant native protocol.

<b>AMQP</b>
Accepts client connections using the Advanced Message Queuing Protocol (AMQP) version 1.0 specification.

<b>HORNETQ</b>
The old core protocol used by HornetQ. Use this to allow legacy HornetQ clients to connect with this ActiveMQ Artemis server. See also the settings <i>multicast prefix</i> and <i>anycast prefix</i> on this acceptor, and the settings <i>incoming interceptors</i> and <i>outgoing interceptors</i> on the server level.

<b>MQTT</b>
Accepts client connections using the Message Queuing Telemetry Transport (MQTT) version 3.1.1 specification.

<b>STOMP</b>
Accepts client connections using the Simple Text Oriented Messaging Protocol (STOMP) version 1.0, 1.1 or 1.2 specification.

By default, any protocol with a loaded module is supported. The CORE protocol module is <i>always</i> loaded when the server starts, other protocol modules are added when you explicitly set the protocol in <i>any</i> of this server's acceptors. For example: when you add one acceptor for just the AMQP protocol and a second acceptor without specifying a protocol, the second acceptor will support both the CORE and AMQP protocols.

<a href="https://activemq.apache.org/artemis/docs/latest/protocols-interoperability.html">Documentation</a>

STOMP consumer credits
When consuming messages in stomp, the server will flow control the channel as messages are acknowledged. The default value is <code>10K</code>. The server won't send more messages than 10K bytes until you ack more messages. 

Notice that if you use auto-ack subscriptions on stomp, you have to consume as fast as you can on your client, or you may flood the channels on Netty what will lead to OutOfMemory errors.

STOMP enable message ID
When receiving Stomp messages via a JMS consumer or a <i>QueueBrowser</i>, the messages have no properties like <i>JMSMessageID</i> by default. However this may bring some inconvenience to clients who wants an ID for their purpose. Artemis Stomp provides a parameter to enable message ID on each incoming Stomp message. If you want each Stomp message to have a unique ID, just set this property to <i>Yes</i>. 

Default is <code>false</code>.

STOMP min large message size
Stomp clients may send very large bodys of frames which can exceed the size of Apache ActiveMQ Artemis server's internal buffer, causing unexpected errors. To prevent this situation from happening, Apache ActiveMQ Artemis provides a stomp configuration attribute stompMinLargeMessageSize. This attribute can be configured inside a stomp acceptor, as a parameter. For example:

 <acceptor name="stomp-acceptor">tcp://localhost:61613?protocols=STOMP;stompMinLargeMessageSize=10240</acceptor>

The type of this attribute is integer. When this attributed is configured, Apache ActiveMQ Artemis server will check the size of the body of each Stomp frame arrived from connections established with this acceptor. If the size of the body is equal or greater than the value of stompMinLargeMessageSize, the message will be persisted as a large message. When a large message is delievered to a stomp consumer, the HorentQ server will automatically handle the conversion from a large message to a normal message, before sending it to the client.
  
If a large message is compressed, the server will uncompressed it before sending it to stomp clients. The default value of stompMinLargeMessageSize is the same as the default value is <code>100KiB</code>.

https://activemq.apache.org/artemis/docs/1.0.0/interoperability.html

Host
This specifies the host name or IP address to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is <code>localhost</code>.

When configuring acceptors, multiple hosts or IP addresses can be specified by separating them with commas. It is also possible to specify <code>0.0.0.0</code> to accept connection from all the host's network interfaces. It's not valid to specify multiple addresses when specifying the host for a connector; a connector makes a connection to one specific address.

Port
This specifies the port to connect to (when configuring a connector) or to listen on (when configuring an acceptor).

The default value for this property is <code>5445</code>.

TCP no delay
If this is <i>Yes</i> then Nagle's algorithm will be enabled.

The default value for this property is <i>Yes</i>.

TCP send buffer size
This parameter determines the size of the TCP send buffer in bytes.

The default value for this property is <code>32768</code> bytes (32KiB). 

TCP buffer sizes should be tuned according to the bandwidth and latency of your network, Here's a good <a href="http://www-didc.lbl.gov/TCP-tuning/"> link</a> that explains the theory behind this.In summary TCP send/receive buffer sizes should be calculated as: buffer_size = bandwidth * RTT. Where bandwidth is in bytes per second and network round trip time (RTT) is in seconds. RTT can be easily measured using the ping utility. For fast networks you may want to increase the buffer sizes from the defaults.

TCP receive buffer size
This parameter determines the size of the TCP receive buffer in bytes.

The default value for this property is <code>32768</code> bytes (32KiB).

Connection TTL
If you need a specific <i>connection TTL</i> for your connections without affecting the <i>connection TTL override</i> setting, you can configure your acceptor with this property, which is used to set the time-to-live for connections that are created from this acceptor.

Connection TTL max
The maximum connection TTL allowed.  The default value for this property is Java's <code>Long.MAX_VALUE</code> meaning there essentially is no max connection TTL by default.

Connection TTL min
The minimum connection TTL allowed. The default value for this property is <code>1000</code> milliseconds

Batch delay
Before writing packets to the transport, Artemis can be configured to batch up writes for a maximum of batch-delay milliseconds. This can increase overall throughput for very small messages. It does so at the expense of an increase in average latency for message transfer.

The default value for this property is <code>0</code> ms.

Cluster connection
If you define more than one cluster connection, you may define what cluster connection will be used to notify topologies. This will be very useful when you are playing with multiple network interface cards (NIC) and need to isolate the cluster definitions.

The default value is the first cluster connection defined at the main configuration.

Use epoll
Enables the use of epoll if a supported linux platform is running a 64bit JVM is detected. Setting this to <i>No</i> will force the use of Java NIO instead of epoll.

Default is <i>Yes</i>.

<a href="https://en.wikipedia.org/wiki/Epoll">Documentation</a>

Use kqueue
Enables the use of kqueue if a supported MacOS platform running a 64bit JVM is detected. Setting this to <i>No</i> will force the use of Java NIO instead of kqueue.

Default is<i>Yes</i>

<a href="https://en.wikipedia.org/wiki/Kqueue">Documentation</a>

Enabled cipher suites
Whether used on an acceptor or connector this is a comma separated list of cipher suites used for SSL communication. The default value is null which means the JVM's default will be used.

Enabled protocols
Whether used on an acceptor or connector this is a comma separated list of protocols used for SSL communication. The default value is null which means the JVM's default will be used.

Write buffer low water mark
This parameter determines the low water mark of the Netty write buffer. Once the number of bytes queued in the write buffer exceeded the high water mark and then dropped down below this value, Netty's channel will start to be writable again. 


Default is <code>32768</code> bytes (32KiB).

Write buffer high water mark
This parameter determines the high water mark of the Netty write buffer. If the number of bytes queued in the write buffer exceeds this value, Netty's channel will start to be not writable. 

Default is <code>131072</code> bytes (128KiB).

Remoting threads
Apache ActiveMQ Artemis will, by default, use a number of threads equal to three times the number of cores (or hyper-threads) as reported by <code>Runtime.getRuntime().availableProcessors()</code> for processing incoming packets. If you want to override this value, you can set the number of threads by specifying this parameter. 
The default value for this parameter is <code>-1</code> which means use the value from <code>Runtime.getRuntime().availableProcessors() * 3</code>.

SSL enabled
Netty SSL is similar to the Netty TCP transport, but it provides additional security by encrypting TCP connections using the Secure Sockets Layer (SSL) / Transport Layer Security (TLS).

The encryption protocols and algorithms supported depend on the Java security provider. The default Oracle/Sun JRE SE 6 provides support for at least the following standards/protocols/algorithms: JCA, JSSE, JCE, SSL v3, TLS v1, SSL v2 Hello, RSA, AES, Blowfish, DES, Triple DES, RC2, RC4, Diffie-Hellman, DSA, X.509, PKIX, PKCS #12, MD2, MD5, SHA-1, SHA-256, SHA-384, SHA-512.

Default is <i>No</i>.

Need client auth
Set to <i>true</i> if SSL needs client authentication.

Default is <i>false</i>.

Want client auth
Default value: <i>No</i>

 Keystore path
The path to the SSL key store on the server which holds the server's certificates (whether self-signed or signed by an authority).

<i>Required</i>

Keystore password
The password of the SSL key store which holds the server's certificates (whether self-signed or signed by an authority).

<i>Required</i>

Keystore provider
If not provided the default is <code>JKS</code>, based on the constant value: <code>DEFAULT_KEYSTORE_PROVIDER</code>.

Truststore path
The path to the trusted client certificate store on the server.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

Truststore password
The password of the trusted client certificate store.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

Truststore provider
If not provided the default is <code>JKS</code> based on value of the constant: <code>DEFAULT_TRUSTSTORE_PROVIDER</code>

Verify host
When used on an acceptor the CN of the connecting client's SSL certificate will be compared to its hostname to verify they match. This is useful only for 2-way SSL.

When used on a connector the CN of the server's SSL certificate will be compared to its hostname to verify they match. This is useful for both 1-way and 2-way SSL.

Default is <i>No</i>.

SSL provider
Used to change the SSL Provider between <code>JDK</code> and <code>OPENSSL</code>. The default value for this property is <code>JDK</code>. 

If used with OPENSSL you can add netty-tcnative to your classpath to use the native installed openssl. This can be useful if you want to use special ciphersuite - elliptic curve combinations which are support through openssl but not through the JDK provider. 

For more information, see <a href="https://en.wikipedia.org/wiki/Comparison_of_TLS_implementations">Documentation</a>



HTTP upgrade enabled
Whether to use the <i>HTTP/1.1 Upgrade header</i> on HTTP connections. In certain situations this might be required, depending on how the incoming HTTP traffic is handled by (for example) your HTTP proxy server.

Default is <i>No</i>.

HTTP response time
How long the server can wait before sending an empty http response to keep the connection alive. 

Only used when HTTP is enabled. Default is <code>10000</code>.

HTTP server scan period
How often, in milliseconds, to scan for clients needing responses. 

Only used when HTTP is enabled. Default is <code>5000</code>.

Direct deliver
When a message arrives on the server and is delivered to waiting consumers, by default, the delivery is done on the same thread as that on which the message arrived. This gives good latency in environments with relatively small messages and a small number of consumers, but at the cost of overall throughput and scalability - especially on multi-core machines. If you want the lowest latency and a possible reduction in throughput then you can use the default value for directDeliver (i.e. <i>Yes</i>). If you are willing to take some small extra hit on latency but want the highest throughput set directDeliver to <i>No</i>.

Incoming max frame size
The maximum length of frame in body. If it exceeds the limit, then the server needs to give the client sends a ERROR, then disconnect the link.

The default value for this property is <code>65536</code>

<>

Heart beat to connection TTL modifier
The <i>heart beat connection TTL modifer</i> is a decimal value that defaults to 2.0 so for example, if a client sends a heart-beat header of 1000,0 the the connection TTL will be set to 2000 so that the data or ping frames sent every 1000 milliseconds will have a sufficient cushion so as not to be considered late and trigger a disconnect

Connections allowed
This limits the number of connections which the acceptor will allow. When this limit is reached a DEBUG level message is issued to the log, and the connection is refused. The type of client in use will determine what happens when the connection is refused. In the case of a core client, it will result in a <code>org.apache.activemq.artemis.api.core.ActiveMQConnectionTimedOutException</code>.




Multicast prefix
Clients can specify a special prefix when connecting to an address to indicate which kind of routing type to use. For example, when using value <code>multicast://</code> for this setting a client could connect to <code>multicast://my.example.address</code> to force multicast routing.

Note: If an acceptor needs to be compatible with HornetQ and/or Artemis 1.x clients, use value <code>jms.topic.</code> here.

<i>Optional</i>

Anycast prefix
Clients can specify a special prefix when connecting to an address to indicate which kind of routing type to use. For example, when using value <code>anycast://</code> for this setting a client could connect to <code>anycast://my.example.address</code> to force anycast routing.

Note: If an acceptor needs to be compatible with HornetQ and/or Artemis 1.x clients, use value <code>jms.queue.</code> here.

<i>Optional</i>

Incoming max frame size
The maximum size of a frame in bytes for incoming messages. When incoming messages are larger than this value, these messages must be splitted up in chunks. If incoming frames exceed this limit, the server logs an error and disconnects. This value applies to the AMQP and STOMP protocol.
 
To prevent errors use the same value as 'Outgoing max frame size' and the maximum frame size on the client side (connection factory).

Default value for this property is <code>65536</code> bytes (64 KiB).

Outgoing max frame size
The maximum size of a frame in bytes for outgoing messages. When messages are larger than this value, these messages will be split up in chunks. This value applies to the AMQP protocol only.
 
To prevent errors use the same value as 'Incoming max frame size' and the maximum frame size on the client side (connection factory).

Default value for this property is <code>131072</code> bytes (128 KiB).

Handshake timeout
Prevents an unauthorised client opening a large number of connections and just keeping them open. As connections each require a file handle this consumes resources that are then unavailable to other clients. Once the connection is authenticated, the usual rules can be enforced regarding resource consumption. 

Default value for this property is set to <code>10</code> seconds. 

Each integer is valid value. When set value to zero or negative integer this feature is turned off. Changing value needs to restart server to take effect.

Backlog
Determines how many un-accepted connections can sit waiting for the application to accept them. By default java uses <code>50</code>

CRL path
Path where the Certificate Revocation List (CRL) is located. A  CRL is a list of certificate serial numbers which have been revoked, are no longer valid, and should not be relied upon by any system user.

Default value for this property is <code>null</code>

