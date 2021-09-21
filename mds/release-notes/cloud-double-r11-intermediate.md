# Release notes for cloud slot template R11 intermediate template

Non service affecting intermediate template to use the R11 double lane release. This is the first of two steps for your upgrade to the new R11 template.

Steps:

1) Use this intermediate template (non service affecting) (duration: 4 minutes)

    - This step will upgrade the backup machines hosted in the second Availability Zone in your cloudslot
    - The network drive containing the Artemis queue store and your Elastic IPs will remain.

2) Use the final template (service affecting) (duration: 4 minutes)

    - This step will upgrade the primary machines in the first Availability Zone in your cloudslot
    - The runtimes on the machines will be restored using the active release in the eMagiz portal

User actions after applying the final template:

- Check if all runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
- Check if messages pass through the bus by verifying a critical message flow in external systems

Features R11 release:

1) Optimize the disk sizes of the eMagiz instances
2) Migrate to the new and faster AWS disk storage GP3 type
