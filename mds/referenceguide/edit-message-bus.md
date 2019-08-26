---
id: edit-message-bus
title: Edit Message Bus
sidebar_label: Edit Message Bus
---
### 
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters or digits).

### 
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

### 
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

### 
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

### 
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

### 
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

### 
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

### 
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

### 
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

### 
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

### 
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


### 
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

---
id: edit-message-bus
title: Edit Message Bus
sidebar_label: Edit Message Bus
---
### 
Abbreviated name of the message bus, with a maximum length of seven characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters or digits).

### 
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

### 
The number of process containers this message bus uses to deploy and run processes.

Using more then one process container will add more processing capacity, redundancy and load balancing of the bus processes to the messaging solution, but also requires more hardware to deploy on.

### 
Whether this message bus uses backup JMS servers that can take over when a live JMS server fails.

Using failover will add high availability and redundancy of the JMS servers to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using failover with only a <i>single</i> container is not very useful, as this makes the container a single point of failure.

### 
The number of backup JMS servers per live JMS server. Normally one should be sufficient, but in some critical situations a "backup for the backup" can be useful.

Using more then one backup will add more redundancy to the messaging solution, but also requires more hardware to deploy on.

### 
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

### 
Whether this message bus uses a cluster of multiple JMS servers to host the message queues.

Using a cluster will add redundancy and load balancing of the JMS queues to the messaging solution, but also requires more hardware to deploy on.

Note that in most cases using a cluster with only a <i>few</i> process containers is not very useful, as the process containers are usually the bottle neck for the total message throughput long before the JMS servers are.

Also note that a cluster does not provide failover behaviour: if a server fails, clients will experience connection problems and messages might be (temporarily) lost. If you want a cluster with failover behaviour, select both <i>use cluster</i> and <i>use failover</i>. This will increase the hardware requirements significantly however, because every JMS server in the cluster needs its own dedicated failover server(s).

### 
The number of JMS servers in the cluster. Every server in the cluster will share the messaging load and host the same message queues (a <i>symmetrical cluster</i>).

### 
The transport type used for creating connections between the JMS clients and JMS servers.

<b>Plain TCP</b>
Normal, unencrypted TCP connections that don't need any SSL certificates.

<b>TCP with SSL</b>
Encrypted TCP connections that need an SSL certificate on the server side. If the certificate is not signed by an official Certificate Authority you'll also need to (manually) add this certificate to the trust store on all clients.

<b>TCP with 2-way SSL</b>
Encrypted TCP connections that need a correct SSL certificate on both the server and the client side. Also, the server certificates need to be added to the trust store of all clients and the client certificates must be added to the trust store of all servers.

### 
By indicating that the (server) certificate is not signed by an official Certificate Authority but is <i>self-signed</i>, properties for specifying the trust store path and password will be used by all clients.

### 
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


### 
A choice for the Infrastructure as a Service determines were the eMagiz runtimes will be deployed.

<b>AWS</b>
Cloud computing platform. Using failover with AWS means that the runtimes are run on stand-by severs, offering a very fast back-up system. In the case of failover, shared store is the default. In the case of no failover there are no back-up servers running, but new servers will be started and set up in a state from before the failure. 

<b>Root</b>
Cloud computing platform. In the case of the use of failover, data replication is the only option.

<b>On-premises</b>
The software is going to be installed locally, on the company's own servers. Does not use the cloud options eMagiz offers.

