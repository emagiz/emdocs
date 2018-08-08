Cluster connection
<a href="https://activemq.apache.org/artemis/docs/latest/clusters.html#configuring-cluster-connections" target="_blank">Documentation</a>

Cluster connections group servers together in order to share message processing load. Each active node in the cluster is an active Artemis server which manages its own messages and handles its own connections.



 Name
All cluster connections must have a unique name in the server.

<i>Required</i>

Address
Each cluster connection only applies to addresses that match this address value. An address is matched on the cluster connection when it begins with the string specified in this field. The address value also supports comma separated lists and an exclude syntax '!'. To prevent an address from being matched on this cluster connection, prepend a cluster connection address string with '!'.

The address can be any value and you can have many cluster connections with different values of address, simultaneously balancing messages for those addresses, potentially to different clusters of servers. By having multiple cluster connections on different addresses a single Artemis server can effectively take part in multiple clusters simultaneously.

Be careful not to have multiple cluster connections with overlapping values of address, e.g. <i>europe</i> and <i>europe.news</i> since this could result in the same messages being distributed between more than one cluster connection, possibly resulting in duplicate deliveries.

Examples:
- <code>eu</code> matches all addresses starting with <i>eu</i>
- <code>!eu</code> matches all address except for those starting with <i>eu</i>
- <code>eu.uk,eu.de</code> matches all addresses starting with either <i>eu.uk</i> or <i>eu.de</i>
- <code>eu,!eu.uk</code> matches all addresses starting with <i>eu</i> but not those starting with <i>eu.uk</i>

Notes:
- Address exclusion will always takes precedence over address inclusion.
- Address matching on cluster connections does not support wild-card matching.


Default is <i>''</i>. Empty string means all addresses

Connector name
The name of the connector which will be sent to other nodes in the cluster so they have the correct cluster topology.

<i>Required</i>

Static connectors
A comma-separated list of connector names defined in the core configuration. The cluster connection will use these connectors to make its initial connection to the cluster. There may be many more servers in the cluster, but these will be discovered via one of these connectors once an initial connection has been made. 

This property or <i>discovery group name</i> must be provided (they are mutually exclusive), but if neither is set an empty list of static connectors is used.

Allow direct connections only
Sometimes you want to define a cluster more explicitly, that is control which servers connect to each other in the cluster. This is typically used to form non symmetrical clusters such as chain cluster or ring clusters. In this case, specify a static list of connectors (not a discovery group), and set this property to <i>Yes</i>. 

By setting <i>allow direct connections only</i> to <i>Yes</i> the cluster connection will only create connections using the statically defined connections, where normally other cluster connections might be discovered after the initial connection is made. 

Default is <i>No</i>.

 Retry interval
This optional parameter determines the period in milliseconds between subsequent reconnection attempts, if the connection to a target node in the cluster has failed. 

This parameter has the same meaning as the <i>retry interval</i> on a bridge. 

Default is <code>500</code> ms.

 Retry interval multiplier
This optional parameter determines a multiplier to apply to the time since the last retry to compute the time to the next retry. This allows you to implement an exponential backoff between retry attempts. 

Let's take an example: If we set retry-interval to 1000 ms and we set retry-interval-multiplier to 2.0, then, if the first reconnect attempt fails, we will wait 1000 ms then 2000 ms then 4000 ms between subsequent reconnection attempts. The default value is 1.0 meaning each reconnect attempt is spaced at equal intervals. 

Default is <code>1.0</code>.

 Max retry interval 
The maximum retry interval in the case a <i>retry interval multiplier</i> has been specified.

Default is <code>2000</code> (2 seconds).

 Reconnect attempts
This optional parameter determines the total number of reconnect attempts the bridge will make before giving up and shutting down. A value of -1 signifies an unlimited number of attempts. 

Default is <code>-1</code>.

Duplicate detection
Internally cluster connections use bridges to link the nodes, and bridges can be configured to add a duplicate id property in each message that is forwarded. If the target node of the bridge crashes and then recovers, messages might be resent from the source node. By enabling duplicate detection any duplicate messages will be filtered out and ignored on receipt at the target node. 

This parameter has the same meaning as <i>use duplicate detection</i> on a bridge. 

Default is <i>Yes</i>.

Message load balancing type
This parameter determines if/how messages will be distributed between other nodes of the cluster. 
If this is set to <it>Off</it> then messages will never be forwarded to another node in the cluster.

If this is set to <it>Strict</it> then each incoming message will be round robin'd even though the same queues on the other nodes of the cluster may have no consumers at all, or they may have consumers that have non matching message filters (selectors). Note that Artemis will not forward messages to other nodes if there are no queues of the same name on the other nodes, even if this parameter is set to <it>Strict</it>. Using Strict is like setting the HornetQ forward-when-no-consumers parameter to <it>true</it>.

If this is set to <it>On demand</it> then Artemis will only forward messages to other nodes of the cluster if the address to which they are being forwarded has queues which have consumers, and if those consumers have message filters (selectors) at least one of those selectors must match the message. Using <it>On demand</it> is like setting the HornetQ forward-when-no-consumers parameter to <it>false</it>.

Default is <it>On demand</it>.



Max hops
When a cluster connection decides the set of nodes to which it might load balance a message, those nodes do not have to be directly connected to it via a cluster connection. Artemis can be configured to also load balance messages to nodes which might be connected to it only indirectly with other Artemis servers as intermediates in a chain. This allows Artemis to be configured in more complex topologies and still provide message load balancing. 

Default is <code>1</code>, which means messages are only load balanced to other Artemis servers which are directly connected to this server.

Confirmation window size
This optional parameter determines the <i>confirmation window size</i> to use for the connection used to forward messages to the target node.

<b>Warning</b>
When forwarding messages from a queue which has a <i>max size bytes</i> set, it's important that <i>confirmation window size</i> is less than or equal to <i>max size bytes</i> to prevent the flow of messages from ceasing. 

Default is <code>1048576</code> (1 MiB).

Min large message size
The size (in bytes) before a message is treated as large. Large messages will be split up and sent in fragments.

Default is <code>102400</code> (100 KiB).

Be aware that you should not use values here that are bigger than the JMS server's <i>journal buffer size</i>, which is <code>501760</code> (490 KiB) by default.

Client failure check period
If the client does not receive any packets for <i>client-failure-check-period</i> milliseconds then it will consider the connection failed and will either initiate failover, or call any FailureListener instances (or ExceptionListener instances if you are using JMS) depending on how it has been configured. 

If you're using JMS it's defined by the ClientFailureCheckPeriod attribute on a HornetQConnectionFactory instance, or if you're deploying JMS connection factory instances direct into JNDI on the server side, you can specify it in the core configuration, using the parameter client-failure-check-period. 

The default value for client failure check period is <code>30000</code> milliseconds, i.e. 30 seconds. A value of -1 means the client will never fail the connection on the client side if no data is received from the server. Typically this is much lower than connection TTL to allow clients to reconnect in case of transitory failure.

Connection TTL
The time to live (in ms) for connections.

The TTL determines how long the server will keep a connection alive in the absence of any data arriving from the client. The client will automatically send "ping" packets periodically to prevent the server from closing it down. If the server doesn't receive any packets on a connection for the connection TTL time, then it will automatically close all the sessions on the server that relate to that connection.

Default is <code>60000</code> (1 minute).

Call timeout 
The timeout (in ms) for remote calls.

Default is <code>30000</code> (30 seconds).

Call failover timeout
Similar to <i>call timeout</i> but used when a call is made during a failover attempt. 

Default is <code>-1</code> (no timeout).

Cluster notification interval
How often (in milliseconds) the cluster connection should broadcast itself when attaching to the cluster. 

Default is <code>1000</code> (1 second).

Cluster notification attempts
How many times the cluster connection should broadcast itself when connecting to the cluster. 

Default is <code>2</code>.

Initial connect attempts
The number of times the system will try to connect a node in the cluster initially. If the max-retry is achieved this node will be considered permanently down and the system will not route messages to this node. Default is -1 (infinite retries).

Producer window size
The size for producer flow control over cluster connection. it's by default disabled through the cluster connection bridge but you may want to set a value if you are using really large messages in cluster. The default value of -1 means no window.

