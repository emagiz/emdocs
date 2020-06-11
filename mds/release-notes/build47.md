Release notes for build number 47
Version 47, released 2020-01-10

Small update that adds support for the new unit testing feature.

New features
- Flows can now be run as a unit test directly from the flow designer in the create phase.

Minor changes
- Added bundle 'com.emagiz.osgi.extender.unittest' 1.0.0
- Updated bundle 'com.emagiz.osgi.extender.core' from 5.1.0 to 5.2.0

Bug fixes
- Fixed an issue in Artemis where connections to the server that are closed immediately, for example those used by AWS load balancer health checks, would not release threads fast enough. This fix should also greatly reduce the number of "AMQ224088: Timeout (10 seconds) while handshaking has occurred" errors in the log.