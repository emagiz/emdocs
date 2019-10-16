Update bringing Artemis/AMQP buses to the GA stage plus adding support for Apache Kafka and WS-Addressing.
## New features
- Artemis/AMQP being the underlying messaging technology for eMagiz buses has reached GA (general availability). All newly created buses will automatically use this new feature and a migration path for existing buses has been made available. The select number of early adopter buses that are already running on Artemis/AMQP are strongly encouraged to update to this build number as well (and 'reset' their infra and JMS server flows) to take advantage of the latest fixes included in this release.
- Client side support for WS-Addressing has been added when calling (SOAP) web services.
- Added support for sending messages to and receiving messages from the Apache Kafka distributed streaming platform.
## Minor changes
- Added bundle 'com.emagiz.bundles.kafka-clients' 0.11.0.3_1
- Added bundle 'com.emagiz.bundles.kafka-streams' 0.11.0.3_1
- Added bundle 'com.emagiz.bundles.spring-integration-kafka' 2.3.0.1
- Added bundle 'com.emagiz.bundles.spring-kafka' 1.3.9.1
- Updated bundle 'com.emagiz.bundles.artemis-server-osgi' from 2.7.0.1 to 2.7.0.2
- Updated bundle 'com.emagiz.components.ws' from 5.0.0 to 5.1.0
## Bug fixes
- Patched Artemis to solve an issue where changes to NFS file locks were not always detected. This could cause problems with failover/failback scenarios in the eMagiz AWS Cloud where Amazon Elastic File System (EFS) is used to store the journal.
