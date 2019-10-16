Small update with important changes for data pipelines and Artemis servers.
## New features
- When writing data to AWS Redshift using data pipelines, you can now configure the duplicate prevention strategy (update, replace, truncate, off). This should make correctly handling duplicate data much easier, since AWS Redshift itself does not handle this at all.
- Added an auto-recovery mechanism to Artemis server that periodically looks for message consumers that seem to be "stuck" and disconnects these, forcing a automatic reconnect. After the reconnect the consumer resumes normal operation and no messages are lost, but message processing for that consumer is halted during the time it takes to detect and recover. This only occurs when consuming large messages, normal messages never get "stuck".
- When serializing messages (i.e. when sending them to a JMS queue or storing them in the channel message store) eMagiz automatically removes any complex headers values that might cause problems on the receiving end. This behaviour has now been extended to include header values such as lists or maps that are fine, but that contain any entries that are not.
- Data pipelines now supports reading items from OData (e.g. Mendix apps) and writing them to AWS Redshift.
## Minor changes
- Updated bundle 'com.emagiz.batch.aws.redshift' from 1.0.0 to 1.1.0
- Updated bundle 'com.emagiz.batch.core' from 1.1.0 to 1.2.0
- Updated bundle 'com.emagiz.osgi.extender.jms' from 1.0.1 to 1.1.0
- Updated bundle 'com.emagiz.components.jdbc' from 5.2.0 to 5.3.0
- Updated bundle 'com.emagiz.components.artemis' from 1.0.1 to 1.1.0
