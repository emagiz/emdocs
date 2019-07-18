---
id: hornetq-jms-server-manager
title: HornetQ JMS server manager
sidebar_label: HornetQ JMS server manager
---
#### Creates a JMS server for hosting JMS queues and topics.
<a href="http://docs.jboss.org/hornetq/2.2.14.Final/user-manual/en/html_single/index.html#using-jms" target="_blank">External documentation</a>



<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#configuring-transports.acceptors" target="_blank">External documentation</a>

Each acceptor defines a way in which connections can be made to the HornetQ server.

Minimal one acceptor is required.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#configuring-transports.connectors" target="_blank">External documentation</a>

Connectors are used by a client to define how it connects to a server.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#clusters" target="_blank">External documentation</a>

Defines a cluster of HornetQ server that share message processing load.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#core-bridges" target="_blank">External documentation</a>

The function of a bridge is to consume messages from a source queue, and forward them to a target address, typically on a different HornetQ server.


Queue configuration settings which will be applied against any addresses with a name that matches a certain wildcard expression.

When <i>match</i> is <code>jms.queue.example</code> for example, the settings would only be applied to any addresses which exactly match the address <code>jms.queue.example</code>. You can also use wildcards to apply settings against many addresses. For example, if you used the match string <code>jms.queue.#</code>, the settings would be applied to all addresses that start with <code>jms.queue.</code> (which would be all JMS queues).

Note that only the most specific match is applied for each address. Some examples from most specific to least specific: <code>jms.queue.example</code> (matches one JMS queue), <code>jms.*.example</code> (matches one JMS queue and one JMS topic), <code>jms.queue.#</code> (matches all JMS queues), <code>jms.#</code> (matches all JMS queues and JMS topics).


Security settings which will be applied against any addresses with a name that matches a certain wildcard expression.

When <i>match</i> is <code>jms.queue.example</code> for example, the settings would only be applied to any addresses which exactly match the address <code>jms.queue.example</code>. You can also use wildcards to apply settings against many addresses. For example, if you used the match string <code>jms.queue.#</code>, the settings would be applied to all addresses that start with <code>jms.queue.</code> (which would be all JMS queues).

Note that only the most specific match is applied for each address. Some examples from most specific to least specific: <code>jms.queue.example</code> (matches one JMS queue), <code>jms.*.example</code> (matches one JMS queue and one JMS topic), <code>jms.queue.#</code> (matches all JMS queues), <code>jms.#</code> (matches all JMS queues and JMS topics).


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#jms-core-mapping" target="_blank">External documentation</a>


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#configuring-transports.acceptors" target="_blank">External documentation</a>


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#persistence" target="_blank">External documentation</a>


#### Persistence enabled
Whether this server is using persistence and store data.

Default is 'true'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#configuring.bindings.journal" target="_blank">External documentation</a>


#### Bindings directory
The file system directory used to store bindings. Relative paths are resolved against the eMagiz data directory.

Default is <code>hornetq/bindings</code>.

#### Create bindings dir
Whether the bindings directory is created on this server startup.

Default is 'true'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#clusters" target="_blank">External documentation</a>


#### Cluster user
The cluster user for this server.

Default is 'HORNETQ.CLUSTER.ADMIN.USER'.

#### Cluster password
The cluster password for this server.

Default is 'CHANGE ME!!'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#undelivered-messages" target="_blank">External documentation</a>


#### Persist delivery count before delivery
Whether delivery count is persisted before messages are delivered to consumers.

Default is 'false'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#undelivered-messages" target="_blank">External documentation</a>


#### Shared store
When using a shared store, both live and backup servers share the <i>same</i> entire data directory using a shared file system. This means the paging directory, journal directory, large messages and binding journal.

When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.

This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). We do not recommend you use Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow).

The advantage of shared-store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation.

The disadvantage of shared store replication is that it requires a shared file system, and when the backup server activates it needs to load the journal from the shared store which can take some time depending on the amount of data in the store.

If you require the highest performance during normal operation, have access to a fast SAN, and can live with a slightly slower failover (depending on amount of data), we recommend shared store high availability.

Default is <code>true</code>.

#### Backup
Whether this server is a backup or not.

Default is <code>false</code>.

#### Backup group name
If set, (remote) backup servers will only pair with live servers with a matching backup group name.

<i>This setting only applies to replicated servers (servers with shared-store can only pair with servers that share the same store).</i>

Default is empty, allowing any backup server to pair with any live server.

#### Allow auto failback
Will this server automatically shutdown if the original live server comes back up.

Default is <code>true</code>.

#### Check for live server
If enabled, during startup a live server will first search the cluster for another server using its node-ID. If it finds one, it will contact this server and try to "fail-back". Since this is a remote replication scenario, the "starting live" will have to synchronize its data with the server running with its ID, once they are in sync, it will request the other server (which it assumes it is a backup that has assumed its duties) to shutdown for it to take over. This is necessary because otherwise the live server has no means to know whether there was a failover or not, and if there was if the server that took its duties is still running or not.

<i>This setting only applies to replicated servers with auto fail-back enabled (servers with shared-store use the shared journal to detect live servers).</i>

Default is <code>true</code>.

#### Failback delay
Failback delay in milliseconds.

Default is <code>5000</code> (5 seconds).

#### Max saved replicated journals size
The maximum number of backup journals to keep after failback occurs.

Default is <code>2</code>.

#### Failover on server shutdown
Whether to cause failover to occur on normal server shutdown. Has no effect when using replication.

Default is <code>false</code>.

#### Replication clustername
Name of the cluster configuration to use for replication. This setting is only necessary in case you configure multiple cluster connections. It is used by replicating backups and by live servers that may attempt fail-back.

<i>This setting only applies to replicated servers (servers with shared-store use the shared journal to detect each other).</i>


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#thread-pooling" target="_blank">External documentation</a>


#### Thread pool max size
The maximum number of threads in the thread pool of this server.

Default is '30'.

#### Scheduled thread pool max size
The maximum number of threads in the scheduled thread pool of this server.

Default is '5'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#management" target="_blank">External documentation</a>


#### JMX management enabled
Whether this server is manageable using JMX or not.

Default is 'true'.

#### JMX domain
The domain used by JMX MBeans (provided JMX management is enabled) for the core components.

Default is 'org.hornetq'.

#### Management address
The management address of this server. Clients can send management messages to this address to manage this server.

The management address requires a special user permission manage to be able to receive and handle management messages.

Default value is 'jms.queue.hornetq.management'.

#### Management notification address
the management notification address of this server. Clients can bind queues to this address to receive management notifications emitted by this server.

Default value is 'hornetq.notifications'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#connection-ttl" target="_blank">External documentation</a>


#### Connection TTL override
The connection time to live. This value overrides the connection time to live sent by the client.

Default is '-1'.

#### Enabled async connection execution
By default, packets received on the server side are executed on the remoting thread.

It is possible instead to use a thread from a thread pool to handle some packets so that the remoting thread is not tied up for too long. However, please note that processing operations asynchronously on another thread adds a little more latency. Please note that most short running operations are always handled on the remoting thread for performance reasons.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#duplicate-detection" target="_blank">External documentation</a>


#### ID cache size
The size of the cache for pre-creating message IDs.

Default is '2000'.

#### Persist ID cache
Whether message ID cache is persisted.

Default is 'true'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#configuring.message.journal" target="_blank">External documentation</a>


#### Journal directory
The directory in which the message journal lives. Relative paths are resolved against the eMagiz data directory.

Default is <code>hornetq/journal</code>.

For the best performance, we recommend the journal is located on its own physical volume in order to minimise disk head movement. If the journal is on a volume which is shared with other processes which might be writing other files (e.g. bindings journal, database, or transaction coordinator) then the disk head may well be moving rapidly between these files as it writes them, thus drastically reducing performance.

When the message journal is stored on a SAN we recommend each journal instance that is stored on the SAN is given its own LUN (logical unit).



#### Create journal dir
If this is set to true then the journal directory will be automatically created at the location specified in journal-directory if it does not already exist. 

Default is 'true'.

#### Journal type
The type of journal used by this server (either 'NIO' or 'ASYNCIO').

Default is 'ASYNCIO'.

#### Journal sync transactional
If this is set to true then HornetQ will make sure all transaction data is flushed to disk on transaction boundaries (commit, prepare and rollback). 

Default is 'true'.

#### Journal sync non transactional
If this is set to true then HornetQ will make sure non transactional message data (sends and acknowledgements) are flushed to disk each time.

Default is 'true'.

#### Journal file size
The size (in bytes) of each journal files.

Default is '10485760' (10 MiB).

#### Journal compact min files
The minimal number of files before we can consider compacting the journal. The compacting algorithm won't start until you have at least this number of files

Default is '10'.

#### Journal compact percentage
The threshold to start compacting. When less than this percentage is considered live data, we start compacting. Note also that compacting won't kick in until you have at least journal-compact-min-files data files on the journal

Default is '30'.

#### Journal min files
The minimum number of files the journal will maintain. When HornetQ starts and there is no initial message data, HornetQ will pre-create journal-min-files number of files.

Creating journal files and filling them with padding is a fairly expensive operation and we want to minimise doing this at run-time as files get filled. By precreating files, as one is filled the journal can immediately resume with the next one without pausing to create it.

Depending on how much data you expect your queues to contain at steady state you should tune this number of files to match that total amount of data.

Default is '2'.

#### Journal max IO
Write requests are queued up before being submitted to the system for execution. This parameter controls the maximum number of write requests that can be in the IO queue at any one time. If the queue becomes full then writes will block until space is freed up. 

The default is 500.

There is a limit and the total max AIO can't be higher than what is configured at the OS level (/proc/sys/fs/aio-max-nr) usually at 65536.

#### Journal buffer timeout
The timeout (in nanoseconds) used to flush buffers in the AIO queue.

Default is '500000' (0.5 millisecond).

#### Journal buffer size
The buffer size (in bytes) for AIO.

Default is '501760' (490 KiB).

#### Journal max IO
The maximum number of write requests for NIO journal.

Default is '1'.

#### Journal buffer timeout
The timeout (in nanoseconds) used to flush buffers in the NIO.

Default is '10000000 / 3' (3.33 milliseconds).

#### Journal buffer size
The buffer size (in bytes) for NIO.

Default is '501760' (490 KiB).


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#paging" target="_blank">External documentation</a>


#### Paging directory
The file system directory used to store paging files. Relative paths are resolved against the eMagiz data directory.

Default is <code>hornetq/paging</code>.

#### Page max concurrent IO
The maximum number of concurrent reads the system can make on paged files. You may increase this parameter depending on the expected number of paged destinations and the limits you have on your disk.

Default is <code>5</code>.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#large-messages" target="_blank">External documentation</a>


#### Large messages directory
The file system directory used to store large messages. Relative paths are resolved against the eMagiz data directory.

Default is <code>hornetq/largemessages</code>.

#### Wildcard routing enabled
Whether wildcard routing is supported by this server.

Default is 'true'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#transaction-config" target="_blank">External documentation</a>


#### Transaction timeout
The timeout (in milliseconds) after which transactions is removed from the resource manager after it was created.

Default is '300000' (5 minutes).

#### Transaction timeout scan period
The frequency (in milliseconds)  to scan transactions to detect which transactions have timed out.

Default is '1000' (1 second).


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#management.message-counters" target="_blank">External documentation</a>


#### Message counter enabled
Whether message counter is enabled for this server.

Default is 'false'.

#### Message counter sample period
The sample period (in milliseconds) to take message counter snapshot.

Default is '10000' (10 seconds).

#### Message counter max day history
The maximum number of days kept in memory for message counter.

Default is '10'.


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#message-expiry" target="_blank">External documentation</a>


#### Message expiry scan period
The frequency (in milliseconds) to scan messages to detect which messages have expired.

Default is '30000' (30 seconds).

#### Message expiry thread priority
The frequency (in milliseconds) to scan messages to detect which messages have expired.

Default is '30000' (30 seconds).


<a href="http://docs.jboss.org/hornetq/2.2.5.Final/user-manual/en/html_single/index.html#security" target="_blank">External documentation</a>


#### Security enabled
Whether security is enabled for this server.

Default is <code>true</code>.

#### Security invalidation interval
The interval time (in milliseconds) to invalidate security credentials, i.e. the maximum time the server is allowed to cache credentials/permissions before calling the security manager again.

Default is <code>10000</code> (10 seconds).

#### Security manager
Reference to a (custom) security manager implementation that can validate user credentials (authentication) and user roles (authorization).

Note that the <i>cluster user</i> of the HornetQ server always has full privileges and the validation of his credentials is done internally (never even reaching the security manager).

#### JMX domain
The domain used by JMX MBeans (provided JMX management is enabled) for the JMS components.

Default is 'org.hornetq'.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

