---
id: tcp-connection-factory
title: TCP connection factory
sidebar_label: TCP connection factory
---
#### Configures a TCP connection factory that can in turn be referenced by other components.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/ip.html#connection-factories" target="_blank">Documentation</a>


#### Type
Connection factories can be <i>client</i> or <i>server</i>.

Client factories open a connection to a server using a host and port.

Server factories listen on a port and create a separate connection for each incoming connection request.

#### Host
The hostname or IP address to which a client connection factory will connect.

#### Port
For client factories, the port to which a client connection factory will connect.

For server factories, the port on which the factory will listen for incoming connections.

#### Serializer
A serializer that converts message payloads to/from output streams/input streams associated with the connection.

Default is <i>byte array CR/LF (de)serializer</i>.

Serializer and deserializer type would normally be the same, but this is not required.

#### Deserializer
A deserializer that converts message payloads to/from output streams/input streams associated with the connection.

Default is <i>byte array CR/LF (de)serializer</i>.

Serializer and deserializer would normally be the same but this is not required.

#### Using NIO
If <i>true</i>, the factory will use <code>java.nio.channel.SocketChannel</code> for communication; for a large number of connections on the server side, this can provide better performance and may use fewer threads.

Using NIO avoids dedicating a thread to read from each socket. For a small number of sockets, you will likely find that not using NIO, together with an async handoff (e.g. to a <i>QueueChannel</i>), will perform as well as, or better than, using NIO.

Consider using NIO when handling a large number of connections. However, the use of NIO has some other ramifications. A pool of threads (in the task executor) is shared across all the sockets; each incoming message is assembled and sent to the configured channel as a separate unit of work on a thread selected from that pool. Two sequential messages arriving on the same socket might be processed by different threads. This means that the order in which the messages are sent to the channel is indeterminate; the strict ordering of the messages on the socket is not maintained.

For some applications, this is not an issue; for others it is. If strict ordering is required, consider setting <i>using-nio</i> to <i>false</i> and using async handoff.

#### SSL context support
A reference to a <code>TcpSSLContextSupport</code> strategy implementation.

Providing this reference enables SSL on connections created by this factory. When this reference is omitted, normal plain text sockets are used.

#### SO keep alive
Whether or not to have socket keep alive turned on.

#### SO linger
Enable/disable <i>SO_LINGER</i> with the specified linger time in seconds. The maximum timeout value is platform specific. The setting only affects socket close.

#### SO receive buffer size
Sets the <i>SO_RCVBUF</i> option to the specified value for this <code>Socket</code>. The <i>SO_RCVBUF</i> option is used by the platform's networking code as a hint for the size to set the underlying network I/O buffers. Increasing the receive buffer size can increase the performance of network I/O for high-volume connection, while decreasing it can help reduce the backlog of incoming data. 

Because <i>SO_RCVBUF</i> is a hint, applications that want to verify what size the buffers were set to should call <code>getReceiveBufferSize()</code>. 

The value of <i>SO_RCVBUF</i> is also used to set the TCP receive window that is advertized to the remote peer. Generally, the window size can be modified at any time when a socket is connected. However, if a receive window larger than 64K is required then this must be requested before the socket is connected to the remote peer. There are two cases to be aware of:
 - For sockets accepted from a <code>ServerSocket</code>, this must be done by calling <code>ServerSocket.setReceiveBufferSize(int)</code> before the <code>ServerSocket</code> is bound to a local address.
 - For client sockets, <code>setReceiveBufferSize()</code> must be called before connecting the socket to its remote peer.

#### SO send buffer size
Sets the <i>SO_SNDBUF</i> option to the specified value for this <code>Socket</code>. The <i>SO_SNDBUF</i> option is used by the platform's networking code as a hint for the size to set the underlying network I/O buffers.

Because <i>SO_SNDBUF</i> is a hint, applications that want to verify what size the buffers were set to should call <code>getSendBufferSize()</code>.

#### SO TCP no delay
Enable/disable <i>TCP_NODELAY</i> (disable/enable Nagle's algorithm).

#### SO timeout
Enable/disable <i>SO_TIMEOUT</i> with the specified timeout, in milliseconds.

With this option set to a non-zero timeout, a <code>read()</code> call on the <code>InputStream</code> associated with this <code>Socket</code> will block for only this amount of time. If the timeout expires, a <code>java.net.SocketTimeoutException</code> is raised, though the <code>Socket</code> is still valid. The option must be enabled prior to entering the blocking operation to have effect. The timeout must be greater than zero. A timeout of zero is interpreted as an infinite timeout.

#### SO traffic class
Sets traffic class or type-of-service octet in the IP header for packets sent from this <code>Socket</code>. As the underlying network implementation may ignore this value applications should consider it a hint.

The traffic class must be in the range <code>0 - 255</code>.

<b>Notes:</b>
For Internet Protocol v4 the value consists of an octet with precedence and TOS fields as detailed in RFC 1349. The TOS field is bitset created by bitwise-or'ing values such the following:
 - <i>IPTOS_LOWCOST</i> (0x02)
 - <i>IPTOS_RELIABILITY</i> (0x04)
 - <i>IPTOS_THROUGHPUT</i> (0x08)
 - <i>IPTOS_LOWDELAY</i> (0x10)

The last low order bit is always ignored as this corresponds to the MBZ (must be zero) bit. 
Setting bits in the precedence field may result in a SocketException indicating that the operation is not permitted. 

As RFC 1122 section 4.2.4.2 indicates, a compliant TCP implementation should, but is not required to, let application change the TOS field during the lifetime of a connection. So whether the type-of-service field can be changed after the TCP connection has been established depends on the implementation in the underlying platform. Applications should not assume that they can change the TOS field after the connection. 

For Internet Protocol v6 tc is the value that would be placed into the <i>sin6_flowinfo</i> field of the IP header.

#### Using direct buffers
If <i>true</i>, instructs the factory to use direct buffers if possible; only applies if <i>using-nio</i> is <i>true</i>. Refer to <code>ByteBuffer</code> javadocs for more information.

#### Single use
If <i>true</i>, a new connection will be created for each use.

For inbound adapters where there is no outbound adapter sharing the factory, the connection will be closed after a message is received.

For outbound adapters where there is no inbound adapter sharing the factory, or for inbound adapters where an outbound adapter shares the factory, the connection will be closed after so-timeout milliseconds.

For outbound adapters where an inbound adapter shares the factory, the connection will be closed after a response is received.

#### Local address
On a multi-homed system, specifies the IP address of the network interface used to communicate.

For inbound adapters and gateways, specifies the interface used to listen for incoming connections. If omitted, the endpoint will listen on all available adapters.

For the UDP multicast outbound adapter specifies the interface to which multicast packets will be sent. For UDP unicast and multicast adapters, specifies which interface to which the acknowledgment socket will be bound.

Does not apply to TCP outbound adapters and gateways.

#### Task executor
Specifies a specific <i>task executor</i> to be used for socket handling. If not supplied, an internal pooled executor will be used.

Needed on some platforms that require the use of specific task executors such as a <code>WorkManagerTaskExecutor</code>. See <i>pool size</i> for thread requirements, depending on other options.

#### Backlog
Specifies the connection backlog for server sockets. Does not apply to client factories.

#### Lookup host
Specifies whether reverse lookups are done on IP addresses to convert to host names for use in message headers. If false, the IP address is used instead.

Default is <i>true</i>.

#### Apply sequence
When set to <i>true</i>, adds <code>sequenceNumber</code> and <code>correlationId</code> headers to messages originating from 
connections created by this factory. Facilitates resequencing if necessary.

Default is <i>false</i>.

#### SSL handshake timeout
The timeout (in seconds) to use while performing handshakes on SSL sockets.

Default is <code>30</code>.

#### Read delay
The delay (in milliseconds) before retrying a read after the previous attempt failed due to insufficient threads.

Default is <code>100</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

