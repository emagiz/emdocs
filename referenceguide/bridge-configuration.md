
Reliably connects two separate HornetQ servers together.
<a href="http://docs.jboss.org/hornetq/2.2.14.Final/user-manual/en/html_single/index.html#core-bridges" target="_blank">Documentation</a>

The function of a bridge is to consume messages from a source queue, and forward them to a target address, typically on a different HornetQ server.

The source and target servers do not have to be in the same cluster which makes bridging suitable for reliably sending messages from one cluster to another, for instance across a WAN, or internet and where the connection may be unreliable.

The bridge has built in resilience to failure so if the target server connection is lost, e.g. due to network failure, the bridge will retry connecting to the target until it comes back online. When it comes back online it will resume operation as normal.

In summary, bridges are a way to reliably connect two separate HornetQ servers together. With a core bridge both source and target servers must be HornetQ servers.

Bridges can be configured to provide once and only once delivery guarantees even in the event of the failure of the source or the target server. They do this by using duplicate detection.


Name
All bridges must have a unique name in the server. 

Required


Queue name
This is the unique name of the local queue that the bridge consumes from, it's a mandatory parameter. The queue must already exist by the time the bridge is instantiated at start-up. 

For example: jms.queue.myname or jms.topic.yourname.

Required


Forwarding address
This is the address on the target server that the message will be forwarded to. If a forwarding address is not specified, then the original address of the message will be retained. 

Default is 'null'.


Filter string
If specified then only messages which match the filter expression specified in the filter string will be forwarded. The filter string follows the 
<a url="http://hornetq.sourceforge.net/docs/hornetq-2.1.2.Final/user-manual/en/html_single/index.html#filter-expressions" target="_blank">HornetQ filter expression syntax</a>. 

Default is 'null'.




Static connectors
A comma-separated list of connector names defined in the core configuration. The bridge will use these connectors to make its connection to the target server or cluster. 

This property or <i>discovery group name</i> must be provided (they are mutually exclusive).


User
This optional parameter determines the user name to use when creating the bridge connection to the remote server. If it is not specified the default cluster user of the configuration will be used. 

Default is 'null'.


Password
This optional parameter determines the password to use when creating the bridge connection to the remote server. If it is not specified the default cluster password of the configuration will be used. 

Default is 'null'.


HA
This optional parameter determines whether or not this bridge should support high availability. <code>true</code> means it will connect to any available server in a cluster and support failover. 

The default value is <code>false</code>.


Discovery group name
This references the name of a discovery group defined in the core configuration. The bridge will use this discovery group to make its connection to the target server(s). 

This property or <i>static connectors</i> must be provided (they are mutually exclusive).


Transformer class name
An optional transformer-class-name can be specified. This is the name of a user-defined class which implements the org.hornetq.core.server.cluster.Transformer interface. 


Retry interval
This optional parameter determines the period in milliseconds between subsequent reconnection attempts, if the connection to the target server has failed. 

Default is '2000'.


Max retry interval
The maximum retry interval in the case a retry-interval-multiplier has been specified.

Default is <code>2000</code> (2 seconds).


Retry interval multiplier
This optional parameter determines a multiplier to apply to the time since the last retry to compute the time to the next retry. This allows you to implement an exponential backoff between retry attempts. 

Let's take an example: If we set retry-interval to 1000 ms and we set retry-interval-multiplier to 2.0, then, if the first reconnect attempt fails, we will wait 1000 ms then 2000 ms then 4000 ms between subsequent reconnection attempts. The default value is 1.0 meaning each reconnect attempt is spaced at equal intervals. 

Default is <code>1.0</code>.


Reconnect attempts
This optional parameter determines the total number of reconnect attempts the bridge will make before giving up and shutting down. A value of <code>-1</code> signifies an unlimited number of attempts.

Default is <code>-1</code>.


Reconnect attempts on same node
The maximum number of reconnect attempts the bridge will make on the same node. A value of <code>-1</code> signifies an unlimited number of attempts.

Default is <code>10</code>.


Use duplicate detection
This optional parameter determines whether the bridge will automatically insert a duplicate id property into each message that it forwards. 

Doing so, allows the target server to perform duplicate detection on messages it receives from the source server. If the connection fails or server crashes, then, when the bridge resumes it will resend unacknowledged messages. This might result in duplicate messages being sent to the target server. By enabling duplicate detection allows these duplicates to be screened out and ignored. 

This allows the bridge to provide a once and only once delivery guarantee without using heavyweight methods such as XA. 

Default is 'true'.


Confirmation window size
This optional parameter determines the confirmation-window-size to use for the connection used to forward messages to the target node. 

WARNING
When using the bridge to forward messages from a queue which has a max-size-bytes set it's important that confirmation-window-size is less than or equal to max-size-bytes to prevent the flow of messages from ceasing. 

Default is '1048576' (1 MiB).


Min large message size
The size (in bytes) before a message is treated as large. Large messages will be split up and sent in fragments.

Default is <code>102400</code> (100 KiB).

Be aware that you should not use values here that are bigger than the JMS server's <i>journal buffer size</i>, which is <code>501760</code> (490 KiB) by default.


Client failure check period
If the client does not receive any packets for client-failure-check-period milliseconds then it will consider the connection failed and will either initiate failover, or call any FailureListener instances (or ExceptionListener instances if you are using JMS) depending on how it has been configured. 

If you're using JMS it's defined by the ClientFailureCheckPeriod attribute on a HornetQConnectionFactory instance, or if you're deploying JMS connection factory instances direct into JNDI on the server side, you can specify it in the core configuration, using the parameter client-failure-check-period. 

The default value for client failure check period is 30000ms, i.e. 30 seconds. A value of -1 means the client will never fail the connection on the client side if no data is received from the server. Typically this is much lower than connection TTL to allow clients to reconnect in case of transitory failure.


Connection TTL
The time to live (in ms) for connections.

The TTL determines how long the server will keep a connection alive in the absence of any data arriving from the client. The client will automatically send "ping" packets periodically to prevent the server from closing it down. If the server doesn't receive any packets on a connection for the connection TTL time, then it will automatically close all the sessions on the server that relate to that connection.

Default is <code>60000</code> (1 minute).

