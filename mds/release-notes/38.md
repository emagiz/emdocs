Small update with important changes for Artemis/AMQP buses.
## New features
- Updated Artemis, Qpid, Proton-J and Netty to the latest maintenance releases. These updates mostly contain bugfixes, improvements and performance wins.
## Minor changes
- Updated bundle 'com.emagiz.bundles.artemis-server-osgi' from 2.6.3.2 to 2.7.0.1
- Updated bundle 'com.emagiz.bundles.netty-buffer' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-codec' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-codec-http' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-codec-mqtt' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-common' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-handler' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-resolver' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-transport' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-transport-native-epoll' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-transport-native-kqueue' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.bundles.netty-transport-native-unix-common' from 4.1.31.1 to 4.1.34.1
- Updated bundle 'com.emagiz.components.artemis' from 1.1.0 to 1.2.0
- Updated bundle 'org.apache.activemq.artemis-amqp-protocol' from 2.6.3 to 2.7.0
- Updated bundle 'org.apache.activemq.artemis-hornetq-protocol' from 2.6.3 to 2.7.0
- Updated bundle 'org.apache.activemq.artemis-hqclient-protocol' from 2.6.3 to 2.7.0
- Updated bundle 'org.apache.activemq.artemis-mqtt-protocol' from 2.6.3 to 2.7.0
- Updated bundle 'org.apache.activemq.artemis-stomp-protocol' from 2.6.3 to 2.7.0
- Updated bundle 'org.apache.activemq.artemis-native' from 2.6.3 to 1.0.0
- Replaced bundle 'org.apache.qpid.jms.client' 0.37.0 with 'com.emagiz.bundles.qpid-jms-client' 0.40.0.1
- Replaced bundle 'org.apache.qpid.proton-j' 0.29.0 with 'com.emagiz.bundles.proton-j' 0.31.0.1
- Removed bundle 'org.jboss.logging.jboss-logging' 3.3.2.Final (replaced by Pax Logging packaged with runtime)
## Bug fixes
- Fixed a critical issue where sending a message with a very specific size could crash the Artemis server ("Can't write records bigger than the bufferSize(501760) on the journal").
## Remarks
- Deployment packages of Artemis based JMS server flows created before this release (build number 37 and lower) can no longer be installed. Flows that have already been installed are not affected, but we strongly recommend to update these as well.
