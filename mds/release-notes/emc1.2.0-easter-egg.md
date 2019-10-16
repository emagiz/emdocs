Update to the eMagiz Mendix Connector (emc), including retry behaviour for exit connectors, libraries updates, and the reintroduction of "emagiz-cleanup-tool.jar".
## New features
- Added a simple retry mechanism to exit connector flows. You can specify "max attempts" and "back-off period", similar to what is available in standard eMagiz flows.
- Reintroduced the "emagiz-cleanup-tool.jar", which helps to solve issues with conflicting versions of libraries in the Mendix "userlib" folder. You should run this tool (located in the "resources" folder of your Mendix app) each time you update the eMagiz Mendix Connector module. Note that this tool cannot solve conflicts caused by other (third-party) Mendix modules containing Java.
# Minor changes
- Libraries updated to the same versions as currently used in the standalone eMagiz runtime (v3.20.0)
  - Update to HornetQ 2.3.25
  - Update to Joda Time 2.7.0
  - Update to Spring Framework 3.2.13
  - Update to Netty 3.6.10
