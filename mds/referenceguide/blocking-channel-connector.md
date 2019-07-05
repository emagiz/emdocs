---
id: blocking-channel-connector
title: Blocking channel connector
sidebar_label: Blocking channel connector
---
#### Blocking channel connector. 
This connector is best used when there are a few very active connections.

This connector uses efficient buffers with a traditional blocking thread model. Direct NIO buffers are used and a thread is allocated per connection.

#### Host
The hostname representing the interface to which this connector will bind, or empty for all interfaces.

#### Port
The port to listen of for connections or <code>0</code> if any available port may be used.

The standard port for the HTTP protocol is <code>80</code>.

<i>Required</i>

