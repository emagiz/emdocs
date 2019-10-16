Service affecting template update to use the R11 release. This is a one step upgrade to the new R11 template.

To use the new R11 release of our cloud template we upgrade in one step, this step will be service affecting.
Steps:
1) Update to the R11 template (service affecting)(duration: 1-4 minutes depending on bus size)
User actions after applying the final template:
- Check if all runtimes are reachable by the runtime dashboard
- Check if all flows end up in the "Active" state
- Check if messages pass through the bus by verifying a critical message flow in external systems

By selecting this template and pressing 'Update AWS' we will update all machines. Your eMagiz services can be unavailable for up to four minutes.

Features:
1) New logging facility for customer support to better monitor machine health
2) Improved email notification to customer support when auto healing is triggered
3) The out-of-memory auto healing is now also triggered by 'garbage collector overhead limit exceeded'
4) Instances now have functional hostnames
5) Java runtime environment is updated to OpenJdk 8u222 (AdoptOpenJDK, 8u222-b10, HotSpot)
