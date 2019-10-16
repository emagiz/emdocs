Major update that switches the underlying messaging technology to use AMQP over Websocket Secure protocol.
## Major changes
- The eMagiz Mendix Connector now connects to the eMagiz bus using the AMQP over WebSocket Secure (amqpwss) protocol. This should be better compatible with most current and future cloud infrastructures. Also, by switching to a standardized protocol, the new eMagiz Mendix Connector provides better forward compatibility with future changes to the eMagiz messaging technology.
- When sending messages asynchronously from Mendix to the eMagiz bus, the eMagiz Mendix Connector buffers these messages internally in case the bus is unreachable. In previous versions these outgoing messages were always stored in an embedded JMS server first, and then forwarded to the eMagiz bus. From this version onwards the eMagiz Mendix Connector no longer contains an embedded JMS server, but uses the Mendix database to temporarily store these messages. Functionally speaking the overall messaging behaviour is the same, but there are some notable differences:
  - Messages are now only stored locally when the connection to the eMagiz bus is down. During normal operations messages are send in real-time, which might (slightly) increase performance.
  - Max limit for locally stored runtime metrics was 5 MiB and is now 1000 messages. In practice this should be quite similar. The maximum for "normal" user-defined messages is still unlimited.
  - A button "queued messages" has been added that shows how many messages are currently stored locally, waiting to be send to the bus. Previously there was no way to to see this.
  - Mendix logging has been added to inform about messages being stored locally. During startup, the number of messages that are still present in the local message store is logged. The message "switching to 'offline' mode: messages are now being stored locally" is logged when the first message cannot be delivered in real-time to the eMagiz bus, and the message "switching back to 'online' mode: all locally stored messages have been send" is logged when the real-time delivery is available again and the full backlog of stored messages has been processed.
  - To reduce the amount of disk space used, all messages are now compressed before storing them locally.
- Changed and updated many dependencies in 'userlib'. Make sure to run the cleanup tool ('resources/emagiz-cleanup-tool.jar') to remove all old dependencies.
  - Replaced HornetQ 2.3.25 with Qpid JMS 0.40.0 and Proton-J 0.31.0
  - Updated Spring Framework from 4.3.8 to 4.3.20
  - Updated Spring Integration from 4.3.9 to 4.3.17
  - Updated Spring Retry from 1.1.5 to 1.2.2
  - Updated Netty from 3.6.10 to 4.1.34
  - Updated JMS spec from 1.1 to 2.0
  - Updated Joda Time from 2.7.0 to 2.10.1
  - Updated Commons Codec from 1.9.0 to 1.11.0
  - Added JTA spec 1.1
  - Removed JBoss Logging 3.1.4
- From this release onwards, Mendix 5 is no longer supported.
## Known issues
- In older versions of the Mendix Desktop Modeler, "emulate cloud security" may cause the eMagiz Mendix connector to fail to connect. This will not occur in the actual cloud. From Mendix 7.21.0 on, this setting has been removed.
## Remarks
- This version is NOT compatible with HornetQ. Be sure to first upgrade your JMS server to accept AMQP connections before using this connector version to connect to it.
- Versions 3.0.0 and 3.0.1 were given out to a select number of early adopter buses, but were never GA releases. These release notes therefore list all cumulative changes since the last public release (version 2.5.0). We strongly recommend upgrading from versions 3.0.0 and 3.0.1, since 3.0.2 contains an important fix: queue prefetch was enabled to prevent large messages getting stuck in queues.
- Version 3.x of the connector is fully compatible with flows build for version 2.x with one exception: the connector infra needs to be updated to switch from HornetQ to AMQP connections. You can simply tell the difference by the build number of the packages: build number 2 is for EMC version 2.x (HornetQ) and build number 3 is for EMC version 3.x (AMQP).
