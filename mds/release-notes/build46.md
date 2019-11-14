Small update that improves Apache Kafka support.
## New features
- Improved the support for sending messages to and receiving messages from the Apache Kafka distributed streaming platform (added in build 39). Instead of configuring the Kafka components using (manually entered) key/value pairs – which is very error-prone – all supported settings now have explicit setter methods. In the flow designer this allowed us to provide users with a nice page showing all available options including validations and help texts.
## Minor changes
- Added bundle 'com.emagiz.components.kafka' 1.0.0
- Added bundle 'com.emagiz.osgi.extender.unittest' 1.0.0
