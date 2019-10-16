Update applying the latest fixes to HornetQ, adding support for Mendix 7 and preparing for AWS Cloud deployments.
## New features
- SNI is now enabled for JMS connections using SSL/TLS. This is required when deploying in the upcoming AWS Cloud.
- Support for Mendix 7: there is a new download available for running the eMagiz connector in Mendix version 7.0.2 or higher. Functionally this connector is identical to the packages for the other Mendix versions.
## Minor changes
- The cleanup tool ('resources/emagiz-cleanup-tool.jar') now shows a list of all dependencies that should be present in your project's userlib directory when no cleanup is required. This list also indicates when such a library seems to be missing.
- Update to HornetQ version 2.3.25.SP16
