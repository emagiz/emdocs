---
id: in-vm-acceptor
title: In VM acceptor
sidebar_label: In VM acceptor
---


# In VM acceptor
Accepts connections from clients that run in the same Java virtual machine as this server.

####  Server ID
Sets the server ID. 

Default is '0'.

####  Buffer pooling
Whether buffer pooling is enabled or not. 
Default values is <i>Yes</i>.

####  Connections allowed
This limits the number of connections which the acceptor will allow. When this limit is reached a DEBUG level message is issued to the log, and the connection is refused. The type of client in use will determine what happens when the connection is refused. In the case of a core client, it will result in a <code>org.apache.activemq.artemis.api.core.ActiveMQConnectionTimedOutException</code>.


####  Cluster connection
If you define more than one cluster connection, you may define what cluster connection will be used to notify topologies. This will be very useful when you are playing with multiple network interface cards (NIC) and need to isolate the cluster definitions.

The default value is the first cluster connection defined at the main configuration.

---
id: in-vm-acceptor
title: In-VM acceptor
sidebar_label: In VM acceptor
---

Accepts connections from clients that run in the same Java virtual machine as this server.

