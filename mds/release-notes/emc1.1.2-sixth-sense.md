The sixth sense release introduces version 6 of the portal.
The major change is an update of the platform to Mendix 5, including styling based on Bootstrap (be sure to empty your browser cache to see the new style, for example by using Ctrl + F5).
Besides that, the graphical representation of the message bus has been upgraded to include more functionality. An example is that you can now zoom out to see the whole picture, or double-click on a process to go directly to the flow.
Another new feature is the new eMagiz Mendix connector, which enables compatibility with the Mendix cloud.
Finally, we fixed several bugs and implemented various minor features.

First public release of the eMagiz Mendix Connector
## New features
- (1.1.0) Instead of using one big configuration, each connector flow can now be deployed, started and stopped independently.
## Minor changes
- (1.1.2) Errors that occur when auto-starting configurations (either during startup or when the user pressed the 'start all' button) are now reported (either in the log or as a message in the web UI). Previously these were silently ignored.
## Bug fixes
- (1.1.1) Fixed validation issue preventing request handler configurations from being updated by a newer version.
