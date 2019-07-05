# Apache ActiveMQ Artemis server
Creates an Apache ActiveMQ Artemis server for hosting message queues.


Each acceptor defines a way in which connections can be made to the Artemis server.

<a href="https://activemq.apache.org/artemis/docs/latest/configuring-transports.html#acceptors" target="_blank">Documentation</a>




Connectors are used by a client to define how to connect to a server. Connectors are also used to create bridges between servers or create clusters of servers.

<a href="https://activemq.apache.org/artemis/docs/latest/configuring-transports.html#connectors" target="_blank">Documentation</a>


Defines a cluster of servers that share message processing load.

<a href="https://activemq.apache.org/artemis/docs/latest/clusters.html#configuring-cluster-connections" target="_blank">Documentation</a>


When <i>match</i> is <code>async.example.message.onramp</code> for example, the settings would only be applied to any addresses which exactly matches the address <code>async.example.message.onramp</code>. You can also use wildcards to apply settings against many addresses. For example, if you used the match string <code>async.#</code>, the settings would be applied to all addresses that start with <code>async.</code> (which would be all asynchronous queues).

Note that only the most specific match is applied for each address. Some examples from most specific to least specific: <code>sync.example.message.onramp</code> (matches one queue), <code>async.example.*.onramp</code> (matches all onramp flow for the <code>example</code> system), <code>async.example.#</code> (matches all synchronous flow for the <code>example</code> system), <code>async.#</code>.

<a href="https://activemq.apache.org/artemis/docs/latest/address-model.html" target="_blank">Documentation</a>


Security settings which will be applied against any addresses with a name that matches a certain wildcard expression.

When <i>match</i> is <code>async.example.message.onramp</code> for example, the settings would only be applied to any addresses which exactly matches the address <code>async.example.message.onramp</code>. You can also use wildcards to apply settings against many addresses. For example, if you used the match string <code>async.#</code>, the settings would be applied to all addresses that start with <code>async.</code> (which would be all asynchronous queues).

Note that only the most specific match is applied for each address. Some examples from most specific to least specific: <code>sync.example.message.onramp</code> (matches one queue), <code>async.example.*.onramp</code> (matches all onramp flow for the <code>example</code> system), <code>async.example.#</code> (matches all synchronous flow for the <code>example</code> system), <code>async.#</code>.

<a href="https://activemq.apache.org/artemis/docs/latest/security.html#role-based-security-for-addresses" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/persistence.html" target="_blank">Documentation</a>



<a href="https://activemq.apache.org/artemis/docs/latest/persistence.html#standard-files" target="_blank">Documentation</a>



When creating connections between nodes of a cluster to form a cluster connection, Artemis uses a cluster user and cluster password.

<a href="https://activemq.apache.org/artemis/docs/latest/clusters.html#cluster-user-credentials" target="_blank">Documentation</a>


In normal use, Artemis does not update delivery count persistently until a message is rolled back (i.e. the delivery count is not updated before the message is delivered to the consumer).

In most messaging use cases, the messages are consumed, acknowledged and forgotten as soon as they are consumed. In these cases, updating the delivery count persistently before delivering the message would add an extra persistent step for each message delivered, implying a significant performance penalty.

<a href="https://activemq.apache.org/artemis/docs/latest/undelivered-messages.html#delivery-count-persistence" target="_blank">Documentation</a>



Artemis has an extensive management API that allows a user to modify a server configuration, create new resources (e.g. addresses and queues), inspect these resources (e.g. how many messages are currently held in a queue) and interact with it (e.g. to remove messages from a queue). Artemis also allows clients to subscribe to management notifications.

<a href="https://activemq.apache.org/artemis/docs/latest/management.html" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/thread-pooling.html" target="_blank">Documentation</a>


Two different strategies for backing up a server are supported: shared store and replication. This configures which strategy a cluster should use to provide the backing up of a servers data. Within this configuration element a server acts either as a master (live), slave (backup).

<a href="https://activemq.apache.org/artemis/docs/latest/ha.html" target="_blank">Documentation</a>



<a href="https://activemq.apache.org/artemis/docs/latest/connection-ttl.html" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/duplicate-detection.html" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/persistence.html#configuring-the-message-journal" target="_blank">Documentation</a>




<a href="https://activemq.apache.org/artemis/docs/latest/paging.html" target="_blank">Documentation</a>



<a href="https://activemq.apache.org/artemis/docs/latest/large-messages.html" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/transaction-config.html" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/management.html#configuring-message-counters" target="_blank">Documentation</a>


The reaper thread will periodically inspect the queues to check if messages have expired.

<a href="https://activemq.apache.org/artemis/docs/latest/message-expiry.html#configuring-the-expiry-reaper-thread" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/security.html" target="_blank">Documentation</a>


You may configure one more addresses that are part of your network topology, that will be pinged through the life cycle of the server. The server will stop itself until the network is back on such case.

<a href="https://activemq.apache.org/artemis/docs/latest/network-isolation.html#pinging-the-network" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/critical-analysis.html" target="_blank">Documentation</a>



<a href="https://activemq.apache.org/artemis/docs/latest/graceful-shutdown.html" target="_blank">Documentation</a>



<a href="https://activemq.apache.org/artemis/docs/latest/protocols-interoperability.html" target="_blank">Documentation</a>


<a href="https://activemq.apache.org/artemis/docs/latest/perf-tuning.html#tuning-the-vm" target="_blank">Documentation</a>


#### Persistence enabled
Whether this server  is using  the file based journal for persistence and store data.

Default is <i>Yes</i>.

####  Bindings directory
The file system directory used to store bindings. Relative paths are resolved against the eMagiz data directory.

Default is <code>artemis/bindings</code>.

####  Create bindings directory
Whether the bindings directory is created on this server startup.

Default is <i>Yes</i>.

####  Cluster user
The cluster user for this server when creating connections between nodes of a cluster to form a cluster connection.

Default is <code>ACTIVEMQ.CLUSTER.ADMIN.USER</code>.

It is imperative that these values are changed from their default, or remote clients will be able to make connections to the server using the default values. If they are not changed from the default, Apache ActiveMQ Artemis will detect this and pester you with a warning on every start-up.

####  Cluster password
The cluster password for this server when creating connections between nodes of a cluster to form a cluster connection.

Default is <code>CHANGE ME!!</code>.

It is imperative that these values are changed from their default, or remote clients will be able to make connections to the server using the default values. If they are not changed from the default, Apache ActiveMQ Artemis will detect this and pester you with a warning on every start-up.

####  Persist delivery count before delivery
Whether the delivery count is persisted before messages are delivered to consumers. False means that this only happens after a message has been cancelled.

Default values is <i>No</i>.

####  Thread pool max size
Maximum number of threads to use for the thread pool. Value <code>-1</code> means 'no limits'.

Default value is <code>30</code>.

####  Scheduled thread pool max size
Maximum number of threads to use for the scheduled thread pool.

Default value is <code>5</code>.

#### JMX  management enabled
Whether this server is manageable using JMX or not.

Default is <i>Yes</i>.

####  JMX domain
The domain used by JMX MBeans (provided JMX management is enabled) for the core components. To manage several Artemis servers from the same MBeanServer, the JMX domain can be configured for each individual Artemis server. 

Default value is <code>org.apache.activemq.artemis</code>.

####  JMX use broker name
Whether the broker name is used as identifier. Using the broker name will avoid clashes when multiple brokers are in a single VM. 

Default value is <i>Yes</i>.

#### Broker name
Identifier for the broker, in this way avoiding clashes when multiple brokers are in a single VM.

Default value is <code>localhost</code>.

#### Management address
The management address of this server. Clients can send management messages to this address to manage this server.

The management address requires a special user permission manage to be able to receive and handle management messages.

Default value is <code>activemq.management</code>.

#### Management notification address
The management notification address of this server. Clients can bind queues to this address to receive management notifications emitted by this server.

Default value is <code>activemq.notifications</code>.

####  Connection TTL override
If set, this will override how long (in ms) to keep a connection alive without receiving a ping. 

Default value is <code>-1</code> (disabled).

####  Connection TTL check interval
The interval (in ms) between connection checks for TTL violations on the broker.

Default value is <code>2000</code> (2 seconds).

####  Enabled async connection execution
Whether code coming from connection is executed asynchronously or not.

Default value is <i>Yes</i>.

#### ID cache size
The size of the cache for pre-creating message IDs.

Default value is <code>2000</code>.

####  Persist ID cache
Whether message ID cache is persisted to the journal.

Default is <i>Yes</i>.

#### Journal Directory
The file system directory used to store journal log.

Default is <code>artemis/journal</code>.

####  Create journal dir
Whether the journal directory is created on this server startup.

Default is <i>Yes</i>.

#### Journal type
The type of journal used by this server. Choosing <i>NIO</i> chooses the Java NIO journal. Choosing <i>AsyncIO</i> chooses the Linux asynchronous IO journal. If you choose <i>AsyncIO</i> but are not running Linux or you do not have libaio installed then Artemis will detect this and automatically fall back to using <i>NIO</i>. Choosing <i>Mapped</i> chooses the Java Memory Mapped journal.

Default is <i>AsyncIO</i>.

####  Journal sync transactional
Whether the journal is synchronized when receiving transactional data. 
If enabled wait for transaction data to be synchronized to the journal before returning response to client. 

Default is <i>Yes</i>.

####  Journal sync non transactional
Whether the journal is synchronized when receiving non-transactional data.

If enabled wait for non transaction data to be synced to the journal before returning response to client. 

Default is <i>Yes</i>.

####  Journal file size
The size (in bytes) of each journal files.

Default is <code>10485760</code> (10 MiB).

####  Journal compact min files
The minimal number of journal files before compacting.

Default is <code>10</code>.

####  Journal compact percentage
The percentage of live data before compacting the journal.

Default is <code>30</code>.

#### Journal min files
How many journal files to pre-create. 

Default is <code>2</code>.

####  Journal datasync
This will disable the use of <i>fdatasync</i> on journal writes. When enabled it ensures full power failure durability, otherwise process failure durability on journal writes (OS guaranteed). This is particular effective for NIO and MAPPED journals, which rely on <i>fsync/msync</i> to force write changes to disk.

Default is <i>Yes</i>.

####  Journal max IO
The maximum number of write requests for AIO journal.

Default is <code>1</code>.

####  Journal buffer timeout
The timeout (in nanoseconds) used to flush buffers in the AIO queue.

Default is <code>500000</code> (0.5 millisecond).

#### Journal buffer size
The buffer size (in bytes) for AIO.

Default is <code>501760</code> (490 KiB).

####  Journal max IO
The maximum number of write requests for NIO journal.

Default is <code>1</code>.

####  Journal buffer timeout 
The timeout (in nanoseconds) used to flush buffers in the NIO.

Default is <code>3333333</code> (3.33 milliseconds).

####  Journal buffer size
The buffer size (in bytes) for NIO.

Default is <code>501760</code> (490 KiB).

####  Journal pool files
The upper theshold of the journal file pool. The system will create as many files as needed however when reclaiming files it will shrink back to the journal-pool-files

Default is <code>-1</code> (no limit).

####  Journal file open timeout
The time (in seconds) to wait when opening a new journal file before failing

Default is <code>5</code>.

####  Journal lock acquisition timeout
How long (in ms) to wait to acquire a file lock on the journal

Default is <code>-1</code> (disabled).

#### Log journal write rate
Whether to log messages about the journal write rate (every 2000 ms).

Default is <i>No</i>.

#### Server dump interval
Interval (in ms) to log server specific information (e.g. memory usage etc).

Default is <code>-1</code> (disabled).

####  Paging directory
The file system directory used to store paging files.

Default is <code>artemis/paging</code>.

####  Page max concurrent IO
The max number of concurrent reads allowed on paging.

Default is <code>5</code>.

####  Max disk usage
The max percentage of data we should use from disks. The system will block while the disk is full.

Default is <code>100</code>.

#### Disk scan period
The interval (in ms) where the disk is scanned for percentual usage. 

Default is <code>5000</code>.

####  Global max size
The amount in bytes before all addresses are considered full. Default is half of the memory used by the JVM (-Xmx argument).

####  Large messages directory
The directory to store large messages.

Default is <code>artemis/largemessages</code>.

####  Transaction timeout
The timeout (in milliseconds) after which transactions is removed from the resource manager after it was created.

Default is <code>300000</code> (5 minutes).

####  Transaction timeout scan period
How often (in ms) to scan for timeout transactions.

Default is <code>1000</code> (1 second).

####  Message counter enabled
Whether message counter is enabled for this server.

Default is <i>No</i>.

#### Message counter sample period
The sample period (in milliseconds) to take message counter snapshot.

Default is <code>10000</code> (10 seconds).

#### Message counter max day history
How many days to keep message counter history.

Default is <code>10</code>.

####  Message expiry scan period
The frequency (in ms) to scan messages to detect which messages have expired.  Set to <code>-1</code> to disable the reaper thread.

Default is <code>30000</code> (30 seconds).

####  Message expiry thread priority
The priority of the thread used to scan message expiration. The reaper thread priority  must be between 1 and 10, 10 being the highest priority.

Default is <code>3</code>.

####  Security enabled
Whether security is enabled for this server.

Default is <i>Yes</i>.

####  Security invalidation interval
The interval time (in milliseconds) to invalidate security credentials.

Default is <code>10000</code> (10 seconds).

####  Populate validated user
Whether or not to add the name of the validated user to the messages that user sends.

For JMS and STOMP clients this is mapped to the key <code>JMSXUserID</code>. For users authenticated based on their SSL certificate this name is the name to which their certificate's DN maps. If security is disabled, then the server will simply use whatever user name (if any) the client provides.

For AMQP messages this setting has no effect.

Default is <i>No</i>.

####  Network check list
This is a comma separated list, no spaces, just DNS or IPs.
   
Warning: Make sure you understand your network topology as this is meant to check if your network is up. Using IPs that could eventually disappear or be partially visible may defeat the purpose. You can use a list of multiple IPs, any successful ping will make the server OK to continue running.

Default is <i>empty</i>.

####  Network check URL list
Use this to use an HTTP server to validate the network.

Default is <i>empty</i>.

####  Network check period
Default is <code>5000</code>.

####  Network check timeout
The timeout to be used on isReachable.

Default is <code>1000</code>.

####  Network check NIC
The NIC (Network Interface Controller) to be used on.

Default is <i>empty</i>.

####  Network check ping command
The command used to oping IPV4 addresses

Default is <code>ping -c 1 -t %d %s</code>.

####  Network check ping6 command
The command used to oping IPV6 addresses

Default is <code>ping6 -c 1 %2$s</code>.

####  Critical analyzer
Enable or disable the critical analysis.

Default is <i>Yes</i>.

#### Critical analyzer timeout
Timeout (in ms) used to do the critical analysis.

Default is <code>120000</code> (2 minutes).

####  Critical analyzer check period
Time used to check the response times.

Default is half of critical-analyzer-timeout.

#### Critical analyzer policy
Should the server log, be halted or shutdown upon failures.

Default is <i>Log</i>.

####  Graceful shutdown enabled
If enabled the server will do a graceful shutdown. 

Default is <i>Yes</i>.

####  Graceful shutdown timeout
Timeout (in ms) on waiting for clients to disconnect before server shutdown. 

Default is <code>-1</code> (wait indefinitely).

####  Resolve protocols
Whether the server uses the serviceLoader to load protocol modules.

Default value is <i>Yes</i>.

####  AMQP use core subscription naming
If enabled use CORE queue naming convention for AMQP.

Default is <i>No</i>.

####  Memory measure interval
Frequency (in ms) to sample JVM memory.
 
Default is <code>-1</code> (memory sampling disabled).

####  Memory warning threshold
Percentage of available memory which will trigger a warning log.

Default is <code>25</code>.

#### Incoming interceptors
Comma-separated list of fully qualified Java class names of interceptors to apply to all incoming network packets.

<i>Optional</i>
<hr/>Use interceptors <code>com.emagiz.fragments.artemis.hornetq.AutoQueueCreator, com.emagiz.fragments.artemis.hornetq.IncomingReplyToConverter</code> to provide compatibility between HornetQ-clients (v2.3.25.SP16) and Artemis-servers (v2.5.0) by attempting to auto-create JMS queues (not topics!) when a client sends a <code>SessionQueueQueryMessage</code> message, and by stripping the <code>jms.queue.</code> prefix from the value of <code>JMSReplyTo</code> headers on incoming messages.

Note that this interceptor is not actually "auto-creating" queues, but uses JMX to achieve something similar. For this reason "auto-delete" will not work for example, and there are probably other slight differences. Another consequence of this is that JMX management must be enabled on the server, and that queues are created with full privileges.

#### Outgoing interceptors
Comma-separated list of fully qualified Java class names of interceptors to apply to all outgoing network packets.

<i>Optional</i>
<hr/>Use interceptors <code>com.emagiz.fragments.artemis.hornetq.TopologyTranslator, com.emagiz.fragments.artemis.hornetq.OutgoingReplyToConverter</code> to provide compatibility between Artemis-servers (v2.5.0) and HornetQ-clients (v2.3.25.SP16) by translating the Netty transport parameters contained in <code>ClusterTopologyChangeMessage</code> messages, and by adding the <code>jms.queue.</code> prefix to the value of <code>JMSReplyTo</code> headers on outgoing messages.

#### Security manager
Reference to a (custom) security manager implementation that can validate user credentials (authentication) and user roles (authorization).

Note that the <i>cluster user</i> of the ActiveMQ Artemis server always has full privileges and the validation of his credentials is done internally (never even reaching the security manager).

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Policy
When using a shared store, both live and backup servers share the <i>same</i> entire data directory using a shared file system. This means the paging directory, journal directory, large messages and binding journal.

When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.

This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). We do not recommend you use Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow).

The advantage of shared-store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation.

The disadvantage of shared store replication is that it requires a shared file system, and when the backup server activates it needs to load the journal from the shared store which can take some time depending on the amount of data in the store.

If you require the highest performance during normal operation, have access to a fast SAN, and can live with a slightly slower failover (depending on amount of data), we recommend shared store high availability.

Default is <i>empty</i> (disabled).

#### Wait for activation
If enabled then server startup will wait until it is activated. If disabled then server startup will be done in the background.

Default is <i>Yes</i>.

#### Restart backup
Will this server, if a backup, restart once it has been stopped because of failback or scaling down.

Default is <i>Yes</i>.

#### Allow fail back
Whether a server will automatically stop when another places a request to take over its place. The use case is when a regular server stops and its backup takes over its duties, later the main server restarts and requests the server (the former backup) to stop operating.

Default is <i>Yes</i>.

#### Check for live server
Whether to check the cluster for a (live) server using our own server ID when starting up. This option is only necessary for performing 'fail-back' on replicating servers. Strictly speaking this setting only applies to live servers and not to backups.

Default is <i>No</i>.

#### Restart backup
Will this server, if a backup, restart once it has been stopped because of failback or scaling down.

Default is <i>Yes</i>.

#### Allow fail back
Whether a server will automatically stop when another places a request to take over its place. The use case is when a regular server stops and its backup takes over its duties, later the main server restarts and requests the server (the former backup) to stop operating.

Default is <i>Yes</i>.

#### Max saved replicated journals size
This specifies how many times a replicated backup server can restart after moving its files on start. Once there are this number of backup journal files the server will stop permanently after if fails back.

Default is <code>2</code>.

#### Failover on server shutdown
Will the backup server come live on a normal server shutdown.

Default is <i>No</i>.

#### Failover on server shutdown
Will the backup server come live on a normal server shutdown.

Default is <i>No</i>.

#### Group name
If set, backup servers will only pair with live servers with matching group name.

#### Cluster name
Name of the cluster configuration to use for replication. This setting is only necessary if you configure multiple cluster connections. If configured then the connector configuration of the cluster configuration with this name will be used when connecting to the cluster to discover if a live server is already running. If unset then the default cluster connections configuration is used (the first one configured).

#### Initial sync timeout
The delay (in milliseconds) to wait before fail-back occurs if we have to start as a replicated server.

Default is <code>30000</code>.

#### Vote on replication failure
By default, if the live server loses its replication connection then it will just carry on and wait for a backup to reconnect and start replicating again. In the event of a possible split brain scenario this may mean that the live stays live even though the backup has been activated.

With this setting it is possible to configure the live server to vote for a quorum if this happens, in this way if the live server doesn't not receive a majority vote then it will shutdown.

Default value is <i>No</i>.

#### Quorum size
It is possible to statically set the quorum size that should be used for the case where the cluster size is known up front.

Default is <code>-1</code> (disabled).

#### Vote retries
How many times we retry a vote before restarting as a backup.

Default is <code>12</code>.

#### Vote retry wait
How long (in milliseconds) do we wait between votes.

Default is <code>5000</code>.

#### Group name
If set, backup servers will only pair with live servers with matching group name.

#### Cluster name
Name of the cluster configuration to use for replication. This setting is only necessary if you configure multiple cluster connections. If configured then the connector configuration of the cluster configuration with this name will be used when connecting to the cluster to discover if a live server is already running. If unset then the default cluster connections configuration is used (the first one configured).

#### Initial sync timeout
The delay (in milliseconds) to wait before fail-back occurs if we have to start as a replicated server.

Default is <code>30000</code>.

#### Vote on replication failure
By default, if the live server loses its replication connection then it will just carry on and wait for a backup to reconnect and start replicating again. In the event of a possible split brain scenario this may mean that the live stays live even though the backup has been activated.

With this setting it is possible to configure the live server to vote for a quorum if this happens, in this way if the live server doesn't not receive a majority vote then it will shutdown.

Default value is <i>No</i>.

#### Quorum size
It is possible to statically set the quorum size that should be used for the case where the cluster size is known up front.

Default is <code>-1</code> (disabled).

#### Vote retries
How many times we retry a vote before restarting as a backup.

Default is <code>12</code>.

#### Vote retry wait
How long (in milliseconds) do we wait between votes.

Default is <code>5000</code>.

