---
id: other
title: Other
sidebar_label: Other
---
#### Name
Name of the flow.

#### Version
The version of the flow.

Uses the <code>major.minor.micro</code> format.

#### Description
Description of this flow.

#### Name
Name of this bus component.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

#### System
The system this offramp process sends messages to.

#### Message type
The type of messages this offramp process handles.

#### Inbox
The JMS queue this offramp process consumes messages from.

#### Outbox
The JMS queue this offramp process produces messages on.

#### Error
The JMS queue this offramp process places error messages on.

#### Name
Name of this bus component.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

#### System
The system this exit connector sends messages to.

#### Message type
The type of messages that are send from the message bus to the connected system by this connector.

#### Inbox
The JMS queue this exit connector consumes messages from.

#### Error
The JMS queue this exit connector places error messages on.

#### Exit/entry connector
Normally, if a system consumes and produces messages, separate entry and exit connector flows are used for connecting the system to the message bus.

In some cases however, the consumption of a message also produces a message as the result. If these messages can be handled by asynchronous message flows but there is a need to somehow correlate them, use an <i>exit/entry connector</i>: this generates an <i>exit connector</i> that delivers messages to the consuming system, that also acts like an <i>entry connector</i> by placing messages produced by that same system back onto the message bus.

#### Message type
The type of messages that are send back to the message bus by this <i>exit/entry connector</i>.

#### Outbox
The JMS queue this <i>exit/entry connector</i> produces messages on that are send back by the connected system.

#### Name
Name of this bus component.

#### Name
Name of this bus component.

#### System
The system that the connector this infra flow is part of connects with.

#### Name
Name of this bus component.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

#### Inbox
The JMS queue this routing process consumes messages from.

#### Error
The JMS queue this routing process places error messages on.

#### Name
Name of this bus component.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

#### Inbox
The JMS queue the error process consumes messages from.

#### Outbox
The JMS queue the error process produces messages on.

Note that these are messages that are handled correctly by the error process, i.e. a valid error message.

#### Error
The JMS queue the error process places error messages on.

Note that this are messages that result in errors while being handled by the error process, i.e. an invalid error message.

#### Name
Name of this bus component.

#### Is backup node
Whether this JMS server is a backup server or not.

#### Cluster name
Name of the cluster this JMS server is part of.

There are two situations where a JMS server is part of a cluster:
 - when using a cluster of JMS servers to share the messaging load
 - when using failover, the live server and all its backups are also placed in a cluster

#### Name
Name of this bus component.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

#### System
The system this onramp process receives messages from.

#### Message type
The type of messages this onramp process handles.

#### Inbox
The JMS queue this onramp process consumes messages from.

#### Outbox
The JMS queue this onramp process produces messages on.

#### Error
The JMS queue this onramp process places error messages on.

#### Name
Name of this bus component.

#### Asynchronous
Whether this message flow is <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

#### System
The system this entry connector receives messages from.

#### Message type
The type of messages that are send from the connected system to the message bus by this connector.

#### Outbox
The JMS queue this entry connector produces messages on.

#### Combined entry connector
Normally, one connector is generated per system that contains multiple <i>entry flows</i> (one for each message type). In some cases however, it is required that all these flows are combined into one big configuration, usually to be able to share resources.

For example, when exposing the connector as a SOAP web service, you'd probably want all different incoming message types to be hosted as different web service operations combined into a <i>single</i> web service (i.e., one HTTP server, one port that needs to be accessible and one WSDL).

#### Type
The type of combined entry connector. This determines how the flows are generated:

<b>SOAP web service</b>: This generates a fully configured Jetty web server hosting a single web service, containing one operation for each message type. The incoming messages are then extracted from the SOAP message and placed on the correct JMS queue.

<b>Custom</b>: This generates a fully configured flow endpoint for each message type, and lets the user define the starting points of these flows.

#### SOAP WS name
Name for the exposed web service as used in the web service URL.

The full URL of the WSDL will look as follows (the underlined words need to be replaced by the actual values):
<code>http://<u>host</u>:<u>port</u>/ws/<u>ws-name</u>/<u>ws-name</u>.wsdl</code>

#### SOAP WS namespace
The namespace for the exposed web service.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

#### Display name
Display name for this message bus.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


#### Nr. of process containers
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

#### Label
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

#### Failover
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware (this includes a SAN) to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

#### Nr. of backup nodes per live node
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

#### Failover type
The strategy to use for backing up a server.

<b><i>Data replication</i></b>
&nbsp;&nbsp;&nbsp;All data synchronization between live and the backup servers is done through network traffic. Therefore all (persistent) data traffic received by the live server will be duplicated to the backup.
&nbsp;&nbsp;&nbsp;Notice that upon startup the backup server will first need to synchronize all existing data from the live server, before becoming capable of replacing the live server should it fail. So unlike the shared store case, a replicating backup will not be a fully operational backup right after start, but only after it finishes synchronizing the data. The time it will take for this to happen will depend on the amount of data to be synchronized and the connection speed.
&nbsp;&nbsp;&nbsp;One issue to be aware of is: in case of a successful failover, the backup's data will be newer than the one at the live's storage. When the live server then restarts, it will synchronize its data with the backup's. If both servers are shutdown however, the administrator will have to determine which one has the lastest data. Shared store doesn't have this issue, because at any moment there is just one copy of the data.
&nbsp;&nbsp;&nbsp;There is one more important distinction between data replication and shared store failover: with shared store, if the backup starts and does not find its live server, the server will just activate and start to serve client requests (this is possible because the shared store is always up to date). In the replication case, the backup just keeps waiting for a live server to pair with (the backup server does not know whether any data it might have is up to date, so it really cannot decide to activate automatically).

<b><i>Shared store</i></b>
&nbsp;&nbsp;&nbsp;Both live and backup servers share the same entire data directory using a shared file system. When failover occurs and a backup server takes over, it will load the persistent storage from the shared file system and clients can connect to it.
&nbsp;&nbsp;&nbsp;This style of high availability differs from data replication in that it requires a shared file system which is accessible by both the live and backup nodes. Typically this will be some kind of high performance Storage Area Network (SAN). The use of Network Attached Storage (NAS), e.g. NFS mounts to store any shared journal (NFS is slow), is not recommended.
&nbsp;&nbsp;&nbsp;The advantage of shared store high availability is that no replication occurs between the live and backup nodes, this means it does not suffer any performance penalties due to the overhead of replication during normal operation. If you require the highest performance during normal operation and have access to a fast SAN, using shared store high availability is recommended.

#### Clustered
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

#### Nr. of nodes in cluster
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

#### Connection type
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

#### Self-signed certificate
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

