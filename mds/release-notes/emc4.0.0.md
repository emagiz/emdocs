Major update that provides Mendix 8 support and removes the web services layer.

New features
- This version of the eMagiz Mendix Connector introduces Pub/Sub technology. By using Pub/Sub, any message published to a topic is immediately received by all of the subscribers to the topic. Please contact your partner manager if you want to make use of this technology.

Major changes
- This version removes the web service layer from the eMagiz Mendix Connector. Mendix now connects to the eMagiz bus directly using Java Actions in microflows. The first upgrade to this new version may take more time for development and testing than previous updates of the eMagiz Mendix Connector. After that, however, it should be easier in use for both Mendix and eMagiz developers. For documentation, please visit the Documentation pages in the Community section of the eMagiz portal.
- This version is only compatible with Mendix version 8.0.0+.
- Removed web service related dependencies from 'userlib'. To prevent errors make sure to run the cleanup tool ('resources/emagiz-cleanup-tool.jar') to remove all old dependencies.
- Removed WSDL4j 1.6.3
- Removed SAAJ Impl 1.3.23
- Removed Extended StAX API 1.7.6

Minor changes
- The Configuration Overview is now a snippet.

Known issues
- The 'single file for container' download from the eMagiz portal contains configurations that are not used anymore ( the request handler and entry and exit configurations).

Remarks
- This version is NOT compatible with HornetQ. Be sure to first upgrade your JMS server to accept AMQP connections before using this connector version to connect to it.