---
id: in-vm-acceptor-transport-configuration
title: In-VM acceptor transport configuration
sidebar_label: In-VM acceptor transport configuration
---
#### Accepts connections from clients running in the same JVM.
Accepts connections from clients that run in the same Java virtual machine as this server.

#### Server ID
Sets the server ID. 

Default is '0'.

#### Cluster connection
If you define more than one cluster connection, you may define what cluster connection will be used to notify topologies. This will be very useful when you are playing with multiple network interface cards (NIC) and need to isolate the cluster definitions.

The default value is the first cluster connection defined at the main configuration.

