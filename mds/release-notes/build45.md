Small update that adds new options for (remotely) deploying flows.
## New features
- The command for (remotely) installing flows on a runtime now also supports automatically starting the flow and uninstalling any other versions, provided that the install command did not fail. These options are now available in your deployment plan but will only work if the infra flow in your runtime has build number 45 (or higher).
## Minor changes
- Updated bundle 'com.emagiz.osgi.extender.jms' from 1.3.0 to 1.3.1
- Updated bundle 'com.emagiz.components.control' from 7.1.0 to 7.2.0
## Bug fixes
- The 'no-op JMS header mapper' (added in build 43) will no longer be replaced by the default header mapper during bean factory post-processing.
