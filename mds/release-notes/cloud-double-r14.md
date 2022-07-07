# Release notes for cloud slot template R14 template

Service affecting final template to use the R14 double lane release.

Process:
To use the new R14 release of our cloud template we upgrade in two steps, with only the second step being service affecting. Below is the remaining step.

Steps:

1) Use the final R14 template (service affecting) (duration: 4 minutes)

User actions after applying the final template:
    - Check if all ".01" runtimes are reachable by the runtime dashboard
    - Check if all flows have been installed according to the active release
    - Check if messages pass through the bus by verifying a critical message flow in external systems

Features R14 release:

1) Move to Python 3.9 version for cloudslot orchestration
2) Better control the unattended updates of instance packages
3) Use new point release of Ubuntu with latest security patches
