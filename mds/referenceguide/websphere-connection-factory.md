---
id: websphere-connection-factory
title: WebSphere connection factory
sidebar_label: WebSphere connection factory
---
#### Creates (non-cached) JMS connections to WebSphere MQ servers.
To use this connection factory, copy the following Java libraries from your <i>WebSphere MQ</i> installation location to the <code>extensions</code> directory of the eMagiz runtime:

- <code>com.ibm.mq.jmqi.jar</code>
- <code>com.ibm.mqjms.jar</code>
- <code>dhbcore.jar</code>

Tested with version 7.1 of <i>WebSphere MQ</i>; should also work with all versions that have a compatible <code>ConnectionFactory</code> interface.

#### Host name
The name of the host.

#### Port
The port for a client connection.

#### Queue manager
The queue manager which is used when selecting a channel definition. This can be in one of the following forms:
 - <code>"qMgrName"</code>, where the actual name of the required queue manager is passed in. The channel must connect to a queue manager of this name.
 - <code>"*qMgrName"</code>, where <code>"*"</code> followed by the actual name of the required queue manager is passed in. The channel definition that is used must specify this queue manager name. This full name is passed onto the queueManager during a connect, but the queue manager that is ultimately connected to may not have the same name as specified here after the <code>"*"</code>.
 - <code>"*"</code> or <code>""</code> or a name which consists entirely of blanks is used. The actual queue manager name is disregarded when a channel definition is being selected.

#### Transport type
Permitted values are:
<b>0</b>: WMQ_CM_BINDINGS
<b>1</b>: WMQ_CM_CLIENT
<b>2</b>: WMQ_CM_DIRECT_TCPIP
<b>4</b>: WMQ_CM_DIRECT_HTTP

#### Channel
The name of the channel; applies to client transport mode only.

#### Username
Optional username that is used for creating connections to the JMS server.

If not set (the default), the handling of user identities when creating connections is controlled by the system property <code>com.ibm.mq.jms.ForceUserID</code> which takes one of two values:
 - <code>false</code>: If an application passes an empty string for the User ID when creating a connection, the empty string is sent to the queue manager for authentication.
 - <code>true</code>: If the application passes an empty string for the User ID when creating a connection, then the User ID that started the JVM will be sent to the queue manager for authentication.

To set this property, applications using the WebSphere MQ classes for JMS need to be started with the following JVM argument:
<code>-Dcom.ibm.mq.jms.ForceUserID=true</code> or
<code>-Dcom.ibm.mq.jms.ForceUserID=false</code>

#### Password
Optional password that is used for creating connections to the JMS server.

Must be provided if and only if the <i>username</i> property is also set.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Description
The description for this connection.

#### Local address
The local address to be used. The format of a local address is <code>[ip-addr][(low-port[,high-port])]</code>.

Some examples:
- <code>9.20.4.98</code>: The channel binds to address 9.20.4.98 locally.
- <code>9.20.4.98(1000)</code>: The channel binds to address 9.20.4.98 locally and uses port 1000.
- <code>9.20.4.98(1000,2000)</code>: The channel binds to address 9.20.4.98 locally and uses a port in the range 1000 to 2000.
- <code>(1000)</code>: The channel binds to port 1000 locally.
- <code>(1000,2000)</code>: The channel binds to a port in the range 1000 to 2000 locally.

You can specify a host name instead of an IP address.

#### Proxy host name
The host name of the proxy server when establishing a real-time connection.

#### Proxy port
The port number of the proxy server when establishing a real-time connection.

#### Client ID
The client ID.

#### SSL cipher suite
The CipherSuite used for SSL encryption. Set this to the CipherSuite matching the CipherSpec set on the SVRCONN channel.

Default is empty, which indicates no SSL encryption is performed.

#### SSL FIPS required
Whether SSLFips (FIPS) is required.

#### SSL peer name
A distinguished name (DN) pattern. If <i>SSL cipher suite</i> is set, this pattern can ensure that the correct queue manager is used. The connection attempt fails if the distinguished name provided by the queue manager does not match this pattern.

This property is ignored if <i>SSL cipher suite</i> is empty.

Default is empty, which indicates no checking of the queue manager's DN pattern is performed.

#### SSL reset count
The SSL reset count. This must be an integer with a value between <code>0</code> (disabled) and <code>999 999 999</code>.

#### Async exceptions
The exception types that should be passed to the user's exception listener.

Permitted values are:
<b>-1</b>: ASYNC_EXCEPTIONS_ALL (default)
<b>1</b>: ASYNC_EXCEPTIONS_CONNECTIONBROKEN

#### Client reconnect options
Specifies the client reconnect options for new connections created by this factory.


Permitted values are:

<b>0</b>: <i>WMQ_CLIENT_RECONNECT_AS_DEF</i> (default)
Use the value specified in the <code>mqclient.ini</code> file. This is set using the <code>DefRecon</code> property within the <code>Channels</code> stanza. It can be set to one of:
 - <code>YES</code>: behaves as the <i>WMQ_CLIENT_RECONNECT</i> option
 - <code>NO</code> (default): does not specify any reconnection options
 - <code>QMGR</code>: behaves as the <i>WMQ_CLIENT_RECONNECT_Q_MGR</i> option
 - <code>DISABLED</code>: behaves as the <i>WMQ_CLIENT_RECONNECT_DISABLED</i> option

<b>16777216</b>: <i>WMQ_CLIENT_RECONNECT</i>
Reconnect to the any of the queue managers specified in the connection name list.

<b>67108864</b>: <i>WMQ_CLIENT_RECONNECT_Q_MGR</i>
Reconnect to the same queue manager we were originally connected to. This will throw MQRC_RECONNECT_QMID_MISMATCH if the queue manager it tries to connect to (specified in the connection name list) has a different QMID to the queue manager originally connected to.

<b>33554432</b>: <i>WMQ_CLIENT_RECONNECT_DISABLED</i>
Reconnection is disabled.

#### Connection name list
Specifies the hosts to which the client will attempt to reconnect to after its connection is broken. The connection name list is a comma seperated list of host/ip port pairs, for example: <code>127.0.0.1(1414),host2.example.com(1400)</code>.

Default is <code>localhost(1414)</code>.

#### Client reconnect timeout
The amount of time (in seconds) that a client connection will attempt to reconnect. After attempting to reconnect for this amount of time, the client will fail with <code>MQRC_RECONNECT_FAILED</code>.

Default is <code>1800</code> (30 minutes).

#### Cleanup interval
The clean up interval (in milliseconds).

#### Cleanup level
The clean up level.

Permitted levels are:
<b>-1</b>: WMQ_CLEANUP_AS_PROPERTY
<b>0</b>: WMQ_CLEANUP_NONE
<b>1</b>: WMQ_CLEANUP_SAFE (default)
<b>2</b>: WMQ_CLEANUP_STRONG
<b>4</b>: WMQ_CLEANUP_NONDUR
<b>3</b>: WMQ_CLEANUP_FORCE

#### Direct auth
The type of direct authentication that is required.

Permitted values are:
<b>0</b>: RTT_DIRECT_AUTH_BASIC
<b>1</b>: RTT_DIRECT_AUTH_CERTIFICATE

#### Fail if quiesce
The default behavior of applications accessing a quiescing queue manager.

Permitted values are:
<b>1</b>: WMQ_FIQ_YES (default)
<b>0</b>: WMQ_FIQ_NO

#### Max buffer size
The maximum buffer size. This is the maximum number of received messages that can be stored in an internal message buffer while waiting to be processed by the client application. This property applies only when using the <code>DIRECT</code> or <code>DIRECTHTTP</code> transport type.

#### Message retention
What happens to unwanted messages.

Permitted values are:
<b>1</b>: WMQ_MRET_YES (default)
<b>0</b>: WMQ_MRET_NO

#### Message selection
Whether the client or the broker performs message selection.

Permitted values are:
<b>0</b>: WMQ_MSEL_CLIENT (default)
<b>1</b>: WMQ_MSEL_BROKER

#### Message batch size
The maximum number of messages to be taken at once when using asynchronous delivery.

#### Multicast
Permitted values are:
<b>0</b>: RTT_MULTICAST_DISABLED (default)
<b>3</b>: RTT_MULTICAST_NOT_RELIABLE
<b>5</b>: RTT_MULTICAST_RELIABLE
<b>7</b>: RTT_MULTICAST_ENABLED

#### Polling interval
The interval (in milliseconds) between scans of all receivers during asynchronous message delivery.

#### Pub ack interval
The number of messages that can be published before requiring acknowledgement from the broker. Applications do not normally alter this value, and must not rely on this acknowledgement.

Default is <code>25</code>.

#### Rescan interval
The interval (in milliseconds) between browsing a queue. The scan looks for messages that were not returned by the previous scan.

#### Send check count
The interval between send calls to check for asynchronous put errors, measured as a count of message sends within a single non-transacted JMS session.

#### Share conv allowed
Whether client connections can share their socket (conversation).

Permitted values are:
<b>0</b>: connections are not allowed to share their socket
<b>1</b>: the connection is allowed to share the socket with other top-level JMS connections from the same process to the same queuemanager, provided that the channel definitions match

#### Status refresh interval
The time (in milliseconds) between transactions to refresh publish/subscribe status.

#### Subscription store
Permitted values are:
<b>0</b>: WMQ_SUBSTORE_QUEUE
<b>1</b>: WMQ_SUBSTORE_BROKER
<b>2</b>: WMQ_SUBSTORE_MIGRATE (default)

#### Syncpoint all GETs
Whether to do all GET operations within a syncpoint.

Default is <code>false</code>.

#### Target client matching
Enables or disables target client matching. If this is set to <code>true</code>, then only MQMD messages (those from a non-JMS application) containing a <i>replyTo</i> will have a JMS <i>replyTo</i> <code>ProviderDestination</code> constructed with <i>targetClient</i> set to <code>1</code> (WMQ_CLIENT_NONJMS_MQ). This ensures that the reply can be understood by the originator.

If this field is set to <code>false</code>, then replies will always contain an RFH2 header, even though the receiver might not understand the reply.

Note that this applies only to point-to-point destinations.

Default is <code>true</code>.

#### Temporary model
The name of the WebSphere MQ model queue. If refers to a model queue that can be used to create a permanent dynamic queue then you must call the <code>MQTemporaryQueue.delete()</code> method to destroy the queue after use.

Within the WebSphere Application Server, <code>MQTemporaryQueue.delete()</code> will be called by the application server when a connection is being closed. Therefore even if a permanent dynamic model queue is used, the created temporary queue will be destroyed.

#### Temp topic prefix
The prefix to use when creating temporary topic names.

When creating temporary topics, JMS will generate a topic string of the form <code>TEMP/&lt;prefix&gt;/&lt;unique id&gt;</code>, or if this property is left with the default value, just <code>TEMP/&lt;unique id&gt;</code>.

#### Temp Q prefix
The prefix to be used to form the name of a WebSphere MQ dynamic queue. This must end with the <code>'*'</code> character.

---
id: websphere-connection-factory
title: WebSphere connection factory
sidebar_label: WebSphere connection factory
---
#### Creates (non-cached) JMS connections to WebSphere MQ servers.
To use this connection factory, copy the following Java libraries from your <i>WebSphere MQ</i> installation location to the <code>extensions</code> directory of the eMagiz runtime:

- <code>com.ibm.mq.jmqi.jar</code>
- <code>com.ibm.mqjms.jar</code>
- <code>dhbcore.jar</code>

Tested with version 7.1 of <i>WebSphere MQ</i>; should also work with all versions that have a compatible <code>ConnectionFactory</code> interface.

#### Host name
The name of the host.

#### Port
The port for a client connection.

#### Queue manager
The queue manager which is used when selecting a channel definition. This can be in one of the following forms:
 - <code>"qMgrName"</code>, where the actual name of the required queue manager is passed in. The channel must connect to a queue manager of this name.
 - <code>"*qMgrName"</code>, where <code>"*"</code> followed by the actual name of the required queue manager is passed in. The channel definition that is used must specify this queue manager name. This full name is passed onto the queueManager during a connect, but the queue manager that is ultimately connected to may not have the same name as specified here after the <code>"*"</code>.
 - <code>"*"</code> or <code>""</code> or a name which consists entirely of blanks is used. The actual queue manager name is disregarded when a channel definition is being selected.

#### Transport type
Permitted values are:
<b>0</b>: WMQ_CM_BINDINGS
<b>1</b>: WMQ_CM_CLIENT
<b>2</b>: WMQ_CM_DIRECT_TCPIP
<b>4</b>: WMQ_CM_DIRECT_HTTP

#### Channel
The name of the channel; applies to client transport mode only.

#### Username
Optional username that is used for creating connections to the JMS server.

If not set (the default), the handling of user identities when creating connections is controlled by the system property <code>com.ibm.mq.jms.ForceUserID</code> which takes one of two values:
 - <code>false</code>: If an application passes an empty string for the User ID when creating a connection, the empty string is sent to the queue manager for authentication.
 - <code>true</code>: If the application passes an empty string for the User ID when creating a connection, then the User ID that started the JVM will be sent to the queue manager for authentication.

To set this property, applications using the WebSphere MQ classes for JMS need to be started with the following JVM argument:
<code>-Dcom.ibm.mq.jms.ForceUserID=true</code> or
<code>-Dcom.ibm.mq.jms.ForceUserID=false</code>

#### Password
Optional password that is used for creating connections to the JMS server.

Must be provided if and only if the <i>username</i> property is also set.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Description
The description for this connection.

#### Local address
The local address to be used. The format of a local address is <code>[ip-addr][(low-port[,high-port])]</code>.

Some examples:
- <code>9.20.4.98</code>: The channel binds to address 9.20.4.98 locally.
- <code>9.20.4.98(1000)</code>: The channel binds to address 9.20.4.98 locally and uses port 1000.
- <code>9.20.4.98(1000,2000)</code>: The channel binds to address 9.20.4.98 locally and uses a port in the range 1000 to 2000.
- <code>(1000)</code>: The channel binds to port 1000 locally.
- <code>(1000,2000)</code>: The channel binds to a port in the range 1000 to 2000 locally.

You can specify a host name instead of an IP address.

#### Proxy host name
The host name of the proxy server when establishing a real-time connection.

#### Proxy port
The port number of the proxy server when establishing a real-time connection.

#### Client ID
The client ID.

#### SSL cipher suite
The CipherSuite used for SSL encryption. Set this to the CipherSuite matching the CipherSpec set on the SVRCONN channel.

Default is empty, which indicates no SSL encryption is performed.

#### SSL FIPS required
Whether SSLFips (FIPS) is required.

#### SSL peer name
A distinguished name (DN) pattern. If <i>SSL cipher suite</i> is set, this pattern can ensure that the correct queue manager is used. The connection attempt fails if the distinguished name provided by the queue manager does not match this pattern.

This property is ignored if <i>SSL cipher suite</i> is empty.

Default is empty, which indicates no checking of the queue manager's DN pattern is performed.

#### SSL reset count
The SSL reset count. This must be an integer with a value between <code>0</code> (disabled) and <code>999 999 999</code>.

#### Async exceptions
The exception types that should be passed to the user's exception listener.

Permitted values are:
<b>-1</b>: ASYNC_EXCEPTIONS_ALL (default)
<b>1</b>: ASYNC_EXCEPTIONS_CONNECTIONBROKEN

#### Client reconnect options
Specifies the client reconnect options for new connections created by this factory.


Permitted values are:

<b>0</b>: <i>WMQ_CLIENT_RECONNECT_AS_DEF</i> (default)
Use the value specified in the <code>mqclient.ini</code> file. This is set using the <code>DefRecon</code> property within the <code>Channels</code> stanza. It can be set to one of:
 - <code>YES</code>: behaves as the <i>WMQ_CLIENT_RECONNECT</i> option
 - <code>NO</code> (default): does not specify any reconnection options
 - <code>QMGR</code>: behaves as the <i>WMQ_CLIENT_RECONNECT_Q_MGR</i> option
 - <code>DISABLED</code>: behaves as the <i>WMQ_CLIENT_RECONNECT_DISABLED</i> option

<b>16777216</b>: <i>WMQ_CLIENT_RECONNECT</i>
Reconnect to the any of the queue managers specified in the connection name list.

<b>67108864</b>: <i>WMQ_CLIENT_RECONNECT_Q_MGR</i>
Reconnect to the same queue manager we were originally connected to. This will throw MQRC_RECONNECT_QMID_MISMATCH if the queue manager it tries to connect to (specified in the connection name list) has a different QMID to the queue manager originally connected to.

<b>33554432</b>: <i>WMQ_CLIENT_RECONNECT_DISABLED</i>
Reconnection is disabled.

#### Connection name list
Specifies the hosts to which the client will attempt to reconnect to after its connection is broken. The connection name list is a comma seperated list of host/ip port pairs, for example: <code>127.0.0.1(1414),host2.example.com(1400)</code>.

Default is <code>localhost(1414)</code>.

#### Client reconnect timeout
The amount of time (in seconds) that a client connection will attempt to reconnect. After attempting to reconnect for this amount of time, the client will fail with <code>MQRC_RECONNECT_FAILED</code>.

Default is <code>1800</code> (30 minutes).

#### Cleanup interval
The clean up interval (in milliseconds).

#### Cleanup level
The clean up level.

Permitted levels are:
<b>-1</b>: WMQ_CLEANUP_AS_PROPERTY
<b>0</b>: WMQ_CLEANUP_NONE
<b>1</b>: WMQ_CLEANUP_SAFE (default)
<b>2</b>: WMQ_CLEANUP_STRONG
<b>4</b>: WMQ_CLEANUP_NONDUR
<b>3</b>: WMQ_CLEANUP_FORCE

#### Direct auth
The type of direct authentication that is required.

Permitted values are:
<b>0</b>: RTT_DIRECT_AUTH_BASIC
<b>1</b>: RTT_DIRECT_AUTH_CERTIFICATE

#### Fail if quiesce
The default behavior of applications accessing a quiescing queue manager.

Permitted values are:
<b>1</b>: WMQ_FIQ_YES (default)
<b>0</b>: WMQ_FIQ_NO

#### Max buffer size
The maximum buffer size. This is the maximum number of received messages that can be stored in an internal message buffer while waiting to be processed by the client application. This property applies only when using the <code>DIRECT</code> or <code>DIRECTHTTP</code> transport type.

#### Message retention
What happens to unwanted messages.

Permitted values are:
<b>1</b>: WMQ_MRET_YES (default)
<b>0</b>: WMQ_MRET_NO

#### Message selection
Whether the client or the broker performs message selection.

Permitted values are:
<b>0</b>: WMQ_MSEL_CLIENT (default)
<b>1</b>: WMQ_MSEL_BROKER

#### Message batch size
The maximum number of messages to be taken at once when using asynchronous delivery.

#### Multicast
Permitted values are:
<b>0</b>: RTT_MULTICAST_DISABLED (default)
<b>3</b>: RTT_MULTICAST_NOT_RELIABLE
<b>5</b>: RTT_MULTICAST_RELIABLE
<b>7</b>: RTT_MULTICAST_ENABLED

#### Polling interval
The interval (in milliseconds) between scans of all receivers during asynchronous message delivery.

#### Pub ack interval
The number of messages that can be published before requiring acknowledgement from the broker. Applications do not normally alter this value, and must not rely on this acknowledgement.

Default is <code>25</code>.

#### Rescan interval
The interval (in milliseconds) between browsing a queue. The scan looks for messages that were not returned by the previous scan.

#### Send check count
The interval between send calls to check for asynchronous put errors, measured as a count of message sends within a single non-transacted JMS session.

#### Share conv allowed
Whether client connections can share their socket (conversation).

Permitted values are:
<b>0</b>: connections are not allowed to share their socket
<b>1</b>: the connection is allowed to share the socket with other top-level JMS connections from the same process to the same queuemanager, provided that the channel definitions match

#### Status refresh interval
The time (in milliseconds) between transactions to refresh publish/subscribe status.

#### Subscription store
Permitted values are:
<b>0</b>: WMQ_SUBSTORE_QUEUE
<b>1</b>: WMQ_SUBSTORE_BROKER
<b>2</b>: WMQ_SUBSTORE_MIGRATE (default)

#### Syncpoint all GETs
Whether to do all GET operations within a syncpoint.

Default is <code>false</code>.

#### Target client matching
Enables or disables target client matching. If this is set to <code>true</code>, then only MQMD messages (those from a non-JMS application) containing a <i>replyTo</i> will have a JMS <i>replyTo</i> <code>ProviderDestination</code> constructed with <i>targetClient</i> set to <code>1</code> (WMQ_CLIENT_NONJMS_MQ). This ensures that the reply can be understood by the originator.

If this field is set to <code>false</code>, then replies will always contain an RFH2 header, even though the receiver might not understand the reply.

Note that this applies only to point-to-point destinations.

Default is <code>true</code>.

#### Temporary model
The name of the WebSphere MQ model queue. If refers to a model queue that can be used to create a permanent dynamic queue then you must call the <code>MQTemporaryQueue.delete()</code> method to destroy the queue after use.

Within the WebSphere Application Server, <code>MQTemporaryQueue.delete()</code> will be called by the application server when a connection is being closed. Therefore even if a permanent dynamic model queue is used, the created temporary queue will be destroyed.

#### Temp topic prefix
The prefix to use when creating temporary topic names.

When creating temporary topics, JMS will generate a topic string of the form <code>TEMP/&lt;prefix&gt;/&lt;unique id&gt;</code>, or if this property is left with the default value, just <code>TEMP/&lt;unique id&gt;</code>.

#### Temp Q prefix
The prefix to be used to form the name of a WebSphere MQ dynamic queue. This must end with the <code>'*'</code> character.

