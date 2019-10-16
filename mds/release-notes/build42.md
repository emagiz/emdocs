Small update that adds aggregation of similar Artemis/HornetQ log messages.
## New features
- Log entries were already being aggregated when 100% identical messages were logged within two minutes. For Artemis and HornetQ logging (i.e. messages starting with "AMQxxxxxx" or "HQxxxxxx" codes) this behaviour has now been changed to also aggregate messages that use identical log codes, but are not 100% identical. Quickly repeating "AMQ222061: Client connection failed, clearing up resources for session 992331fa-98f9-11e9-8ce6-d3ddf5cbf016" warnings for example should no longer clog up your JMS server logs.
## Minor changes
- Updated bundle 'com.emagiz.components.logging' from 6.2.0 to 6.3.0
