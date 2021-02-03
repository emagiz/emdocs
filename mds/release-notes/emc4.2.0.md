Version emc 4.2.0, released 2021-01-21

Update which brings automatic connector-infra configuration downloading, improved exception handling, and dependency updates.

Major changes
- On project startup the connector-infra configuration is downloaded, installed, and started automatically.
- When it is not possible to retrieve the active release, the previous connector-infra will be used.
- The Configuration Overview snippet is not necessary anymore and therefore removed from the module.

Minor changes
- Improved exception handling for synchronous entry integrations.
- Standard eMagiz bus exceptions are recognized and converted into Mendix exceptions.
- Updated dependencies in 'userlib'. To prevent errors, run the cleanup tool ('resources/emagiz-cleanup-tool.jar') to remove all old dependencies.
- Updated Spring Framework from version 4.3.20 to version 5.2.3
- Updated Netty from version 4.1.34 to version 4.1.50
- Updated Proton-J from version 0.31.0 to version 0.33.5
- Updated Spring Retry from version 1.2.2 to version 1.2.5
- Updated Joda Time from version 2.10.1 to version 2.10.5