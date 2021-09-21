# Release notes for cloud slot template R11 template

Service affecting final template to use the R11 double lane release.

Process:
To use the new R11 release of our cloud template we upgrade in two steps, with only the second step being service affecting. Below is the remaining step.

Steps:

1) Use the final R11 template (service affecting)(duration: 4 minutes)

User actions after applying the final template:
    - Check if all ".01" runtimes are reachable by the runtime dashboard
    - Check if all flows have been installed according to the active release
    - Check if messages pass through the bus by verifying a critical message flow in external systems

Features R11 release:

1) Optimize the disk sizes of the eMagiz instances
2) Migrate to the new and faster AWS disk storage GP3 type
