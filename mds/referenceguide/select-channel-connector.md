---
id: select-channel-connector
title: Select channel connector
sidebar_label: Select channel connector
---
#### Select channel connector.

This connector is best used when there are a many connections that have idle periods.

This connector uses efficient buffers with a non blocking threading model. Direct buffers are used and threads are only allocated to connections with requests. Synchronization is used to simulate blocking for the servlet API, and any unflushed content at the end of request handling is written asynchronously.



#### Host
The hostname representing the interface to which this connector will bind, or empty for all interfaces.

#### Port
The port to listen of for connections or <code>0</code> if any available port may be used.

The standard port for the HTTP protocol is <code>80</code>.

<i>Required</i>

