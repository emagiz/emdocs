Qpid AMQP connection factory
Creates a Qpid JMS client connection factory. This can be used to connect to (remote) servers using the AMQP protocol. Advanced Message Queuing Protocol (AMQP) is an open internet protocol for reliably sending and receiving messages.

<a href="https://qpid.apache.org/overview.html" target="_blank">Documentation</a>


The Prefetch Policy controls how many messages the broker can send to the client and be held in a prefetch buffer for each consumer instance.

Prefeching messages can speed up message processing since there will always be messages waiting on the client as opposed to having to wait after every message acknowledgement for the broker to send another message.

However, if you use the default value you will probably not see desirable behaviour in the following cases:

1) When using Session.Transacted and the session is rollback, the message that was received and failed to be processed is sent back to the server as well as all the mesages in the buffer. Meaning that when the number of max redeliveries for the first failed message is reached, also the messages in the buffer will have reach the same number of redeliveries and will be removed from the queue even if they were not actually processed by the client.

2) When using a Competing Consumers pattern, prefetch can give the appearance of unequal division of work. 

3) When message size is large and you do not wish the memory footprint of the application to grow (or suffer an OutOfMemoryError).

4) When using special queue types (such as LVQs, Sorted Queue and Priority Queues). 

To disabled message buffering set 0. This will cause the consumer to poll for messages, one at a time, without caching on the client.

Large prefetch values are recommended for high performance with high message volumes. However, for lower message volumes, where each message takes a long time to process, the prefetch should be set to 1. This ensures that a consumer is only processing one message at a time.


The Redelivery Policy controls how redelivered messages are handled on the client.


The MessageID Policy controls the type of the Message ID assigned to messages sent from the client.


The Presettle Policy controls when a producer or consumer instance will be configured to use AMQP presettled messaging semantics.


The Deserialization Policy provides a means of controlling which types are trusted to be deserialized from the object stream while retrieving the body from an incoming JMS ObjectMessage composed of serialized Java Object content. This allows specifying a whitelist and a blacklist of Java class or package names.

By default, all types are trusted during attempt to deserialize the body.


With failover enabled the client can reconnect to another server automatically when connection to the current server is lost for some reason. In addition, this can be used distribute client connections more evenly across multiple remote peers in a clustered setup.


Default connection settings that will be used for any of the connectors. These settings can be overriden for each connector individually.


Connection settings for each individual connector that can be used by this connection factory. At least the host and port have to be specified.

Failover
With failover enabled the client can reconnect to another server automatically when connection to the current server is lost for some reason. In addition, this can be used distribute client connections more evenly across multiple remote peers in a clustered setup.


Default connection settings that will be used for any of the connectors. These settings can be overriden for each connector individually.

Use SSL
Enable SSL to secure connections.

Default is false.

Use WebSocket
Enable the WebSocket protocol.

Default is false

Username
Username value used to authenticate the connection.

<i>Required</i>

Password
The password value used to authenticate the connection.

<i>Required</i>

Initial reconnect delay
The amount of time in milliseconds that the client will wait before the first attempt to reconnect to a remote peer.

The default value is zero, meaning the first attempt happens immediately.

Reconnect delay
Controls the delay in milliseconds between successive reconnection attempts. If the backoff option is not enabled this value remains constant.

Defaults to10 milliseconds.

Max reconnect delay
The maximum time in milliseconds that the client will wait before attempting a reconnect. This value is only used when the backoff feature is enabled to ensure that the delay does not grow too large.

Defaults to 30000 milliseconds (30 seconds) as the max time between connect attempts.

Use reconnect backoff
Controls whether the time between reconnection attempts should grow based on a configured multiplier.

Defaults to true.

Reconnect backoff multiplier
The multiplier used to grow the reconnection delay value.

Defaults to 2.

Max reconnect attempts
The number of reconnection attempts allowed before reporting the connection as failed to the client.

The default is no limit (-1).

Startup max reconnect attempts
For a client that has never connected to a remote peer before, this option controls how many attempts are made to connect before reporting the connection as failed.

The default is to use the value of maxReconnectAttempts.

Warn after reconnect attempts
Controls how often the client will log a message indicating that failover reconnection is being attempted.

The default is to log every 10 connection attempts.

Randomize connection order
When true, the set of connectors is randomly shuffled prior to attempting to connect to one of them. This can help to distribute client connections more evenly across multiple remote peers in a clustered situation.

The default value is false.

AMQP Open server list action
Controls how the failover transport behaves when the connection Open frame from the remote peer provides a list of failover hosts to the client.

If REPLACE is configured, then all failover URIs other than the one for the current server are replaced with those provided by the remote peer.
If ADD is configured, then the URIs provided by the remote are added to the existing set of failover URIs, with de-duplication.
If IGNORE is configured, then any updates from the remote are dropped and no changes are made to the set of failover URIs in use.

Default is REPLACE.

Force async send
Configures whether all Messages sent from a MessageProducer are sent asynchronously or only those Message that qualify such as Messages inside a transaction or non-persistent messages.

Force sync send
Override all asynchronous send conditions and always sends every Message from a MessageProducer synchronously.

Force async acks
Causes all Message acknowledgments to be sent asynchronously.

Local message expiry
Controls whether MessageConsumer instances will locally filter expired Messages or deliver them. 

By default this value is set to true and expired messages will be filtered.

Local message priority
If enabled, prefetched messages are reordered locally based on their given Message priority value.

Default is false.

Validate property names
Wether message property names should be validated as valid Java identifiers.

Default is true.

Receive local only
If enabled, receive calls with a timeout will only check a consumers local message buffer, otherwise, the remote peer is checked to ensure there are really no messages available if the local timeout expires before a message arrives.

Default is false, the remote is checked.

ReceiveNoWait local only
If enabled, receiveNoWait calls will only check a consumers local message buffer, otherwise, the remote peer is checked to ensure there are really no messages available.

Default is false, the remote is checked.

Queue prefix
Optional prefix value added to the name of any Queue created from a JMS Session.

Topic prefix
Optional prefix value added to the name of any Topic created from a JMS Session.

Close timeout
Timeout value in milliseconds that controls how long the client waits on resource closure before returning.

By default the client waits 60000 milliseconds (60 seconds) for a normal close completion event.

Connect timeout
Timeout value in milliseconds that controls how long the client waits on Connection establishment before returning with an error.

By default the client waits 15000 milliseconds (15 seconds) for a connection to be established before failing.



Send timeout
Timeout value in milliseconds that controls how long the client waits on completion of a synchronous message send before returning an error.

By default the client will wait indefinitely for a send to complete.

Request timeout
Timeout value in milliseconds that controls how long the client waits on completion of various synchronous interactions, such as opening a producer or consumer, before returning an error. Does not affect synchronous message sends.

By default the client will wait indefinitely for a request to complete.

ClientID
The pre-configured client ID for the connection factory.

ClientID prefix
Optional prefix value that is used for generated Client ID values when a new Connection is created for the JMS ConnectionFactory.

The default prefix is 'ID:'.

Connection ID prefix
Optional prefix value that is used for generated Connection ID values when a new Connection is created for the JMS ConnectionFactory. This connection ID is used when logging some information from the JMS Connection object so a configurable prefix can make breadcrumbing the logs easier.

The default prefix is 'ID:'.

Populate JMSXUserID
Controls whether a MessageProducer will populate the JMSXUserID value for each sent message using the authenticated username from the connection.

This value defaults to false and the JMSXUserID for all sent message will not be populated.

Await ClientID
Controls whether a Connection with no ClientID configured in the URI will wait for a ClientID being set programatically (or the connection being used otherwise to signal none can be set) before sending the AMQP connection Open.

Defaults to true.

Use daemon thread
Controls whether a Connection will use a daemon thread for its executor.

Defaults to false to ensure a non-daemon thread is present by default.

_queue_prefetch
Defaults to 1000

_topic_prefetch
Defaults to 1000

_queue_browser_prefetch
Defaults to 1000

_durable_topic_prefetch
Defaults to 1000

_max_redeliveries
Controls when an incoming message is rejected based on the number of times it has been redelivered. A value of zero would indicate no message redeliveries are accepted, a value of five would allow a message to be redelivered five times, etc.

The default value is (-1) disabled.

_redelivery_outcome
Controls the outcome that is applied to a message that is being rejected due to it having exceeded the configured maxRedeliveries value. 

The default outcome value is MODIFIED_FAILED_UNDELIVERABLE.

_message_id_type
The MessageID Policy controls the type of the Message ID assigned to messages sent from the client.

By default a generated String value is used for the MessageID on outgoing messages. 

_presettle_all
The Presettle Policy controls when a producer or consumer instance will be configured to use AMQP presettled messaging semantics.

When true all producers and non-transacted consumers created operate in presettled mode, 

Defaults to false.

_presettle_producers
When true all producers operate in presettled mode.

Defaults to false.

_presettle_topic_producers
When true any producer that is sending to a Topic or Temporary Topic destination will operate in presettled mode

Defaults to false.

_presettle_queue_producers
When true any producer that is sending to a Queue or Temporary Queue destination will operate in presettled mode.

Defaults to false.

_presettle_transacted_producers
When true any producer that is created in a transacted Session will operate in presettled mode.

Defaults to false.

_presettle_consumers
When true all consumers operate in presettled mode.

Defaults to false.

_presettle_topic_consumers
When true any consumer that is receiving from a Topic or Temporary Topic destination will operate in presettled mode.

Defaults to false.

_presettle_queue_consumers
When true any consumer that is receiving from a Queue or Temporary Queue destination will operate in presettled mode.

Defaults to false.

Whitelist
A comma separated list of class/package names that should be allowed when deserializing the contents of a JMS ObjectMessage, unless overridden by the blackList. The names in this list are not pattern values, the exact class or package name must be configured, e.g "java.util.Map" or "java.util". Package matches include sub-packages.

Default is to allow all. 

Blacklist
A comma separated list of class/package names that should be rejected when deserializing the contents of a JMS ObjectMessage. The names in this list are not pattern values, the exact class or package name must be configured, e.g "java.util.Map" or "java.util". Package matches include sub-packages.

Default is to prevent none.


SSL
_use_ssl
Enable SSL to secure connections.

Default is false.

 Key store location
This is the path to the SSL key store on the client which holds the client certificates. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.keyStore".

Key store password
This is the password for the SSL key store on the client which holds the client certificates. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.keyStorePassword"

Trust store location
This is the path to the trusted client certificate store on the server. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.trustStore".

Trust store password
This is the password to the trusted client certificate store on the server. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.trustStorePassword"

Custom key store
Whether or not to use an explicitly set custom (file)path, or select a SSL store from the flow's resources.

Default is false (select from the resources).

Custom trust store
Whether or not to use an explicitly set custom (file)path, or select a SSL store from the flow's resources.

Default is false (select from the resources).

Key store
This is the SSL key store on the client which holds the client certificates. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.keyStore".

Key store
This is the trusted client certificate store on the server. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.trustStore".

Trust store type
The type of trustStore being used.

Default is to read from the system property "javax.net.ssl.trustStoreType". If not set, then default is "JKS".

Key store type
The type of keyStore being used.

Default is to read from the system property "javax.net.ssl.keyStoreType". If not set, then default is "JKS".

Context protocol
The protocol argument used when getting an SSLContext.

Default is "TLS".

Trust all
Whether to trust the provided server certificate implicitly, regardless of any configured trust store.

Defaults to false.

Key alias
The alias to use when selecting a keypair from the keystore if required to send a client certificate to the server.

No default.


Default connection settings
Send buffer size
The send buffer size in bytes. The value must be greater than zero or an <code> IllegalArgumentException</code> will be thrown.

The default value for this property is 65536 bytes (64KiB).

Receive buffer size
This parameter determines the size of the TCP receive buffer in bytes. The value must be greater than zero or an <code>IllegalArgumentException</code> will be thrown.

The default value for this property is 65536 bytes (64KiB).

Traffic class
The traffic class value used by the TCP connection. A valid value should be between 0 and 255.

Default is 0.

Connection timeout
The timeout (in milliseconds) for creating connections to the specified server. 

Default is 60000 milliseconds (60 seconds).

Socket timeout
The socket's timeout in milliseconds on blocking socket operations.

With this option set to a non-zero timeout, a read() call on the InputStream associated with this Socket will block for only this amount of time. If the timeout expires, a <code>java.net.SocketTimeoutException </code> is raised, though the Socket is still valid. The option must be enabled prior to entering the blocking operation to have effect. The timeout must be > 0. A timeout of zero is interpreted as an infinite timeout.

Default value is -1 (disabled).


Socket linger
The socket's linger on close timeout value in seconds.

This option disables/enables immediate return from a close() of a TCP Socket. Enabling this option with a non-zero Integer timeout means that a close() will block pending the transmission and acknowledgement of all data written to the peer, at which point the socket is closed gracefully. Upon reaching the linger timeout, the socket is closed forcefully, with a TCP RST. Enabling the option with a timeout of zero does a forceful close immediately. If the specified timeout value exceeds 65,535 it will be reduced to 65,535.

Default is -1 (disabled).

TCP keep alive
Enables the TCP keep alive value to prevent connections from timing out at the TCP level.

For more information, see <a href="http://tldp.org/HOWTO/TCP-Keepalive-HOWTO/overview.html">Documentation</a>

Default is false.

TCP no delay
Default is true.

Use Epoll layer
When true, the transport will use the native Epoll layer when available, instead of the NIO layer, which can improve performance.

Defaults to true.

Use KQueue layer
When true, the transport will use the native KQueue layer when available, instead of the NIO layer, which can improve performance.

Defaults to false.

Enabled cipher suites
The cipher suites to enable, comma separated. Any disabled ciphers are removed from this.

No default, meaning the context default ciphers are used.

Disabled cipher suites
The cipher suites to disable, comma separated. Ciphers listed here are removed from the enabled ciphers.

No default.

Enabled protocols
The protocols to enable, comma separated. Any disabled protocols are removed from this.

No default, meaning the context default protocols are used.

Disabled protocols
The protocols to disable, comma separated. Protocols listed here are removed from the enabled protocols.

Default is "SSLv2Hello,SSLv3".

Verify host
Whether to verify that the hostname being connected to matches with the provided server certificate.

Defaults to true.

Use SASL  layer
Controls whether connections should use a SASL layer or not.

Default is true.

SASL mechanisms
Which SASL mechanism(s) the client should allow selection of, if offered by the server and usable with the configured credentials. Comma separated if specifying more than 1 mechanism. The clients supported mechanisms are currently EXTERNAL, SCRAM-SHA-256, SCRAM-SHA-1, CRAM-MD5, PLAIN, ANONYMOUS.

Default is to allow selection from all those mechanisms.

Idle timeout
The idle timeout in milliseconds after which the connection will be failed if the peer sends no AMQP frames.

Default is 60000 milliseconds.

vhost
The vhost to connect to. Used to populate the Sasl and Open hostname fields.

Default is the main hostname from the Connection URI.

Max frame size
The maximum size of frames in bytes for outgoing and incoming messages. When messages are larger than this value, these messages must be splitted up in chunks.
 
If incoming websocket frames exceed this limit, then this client logs an error and disconnects. This may occur in message gateways, where messages are pushed to this connection factory.
 
To prevent errors when websockets are enabled, use the same value as the incoming and outgoing max frame size on the server side.

Default value for this property is <code>1048576</code> bytes (1 MiB).

Drain timeout
The time in milliseconds that the client will wait for a response from the remote host when a consumer drain request is made. If no response is seen in the allotted timeout period, the link will be considered failed and the associated consumer will be closed.

Default is 60000 milliseconds.

Allow non-secure redirects
Controls whether an AMQP connection will allow for a redirect to an alternative host over a connection that is not secure when the existing connection is secure, e.g. redirecting an SSL connection to a raw TCP connection.

Default is false.

Id
Name that uniquely identifies this flow component.

<i>Required</i>

