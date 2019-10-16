Service affecting template update to use the R10 release. This is a one step upgrade to the new R10 template.

To use the new R10 release of our cloud template we upgrade in one step, this step will be service affecting.
Steps:
1) Update to the R10 template (service affecting)(duration: 1-4 minutes depending on bus size)
User actions after applying the final template:
- Check if all runtimes are reachable by the runtime dashboard
- Check if all flows end up in the "Active" state
- Check if messages pass through the bus by verifying a critical message flow in external systems

By selecting this template and pressing 'update AWS' we will update all machines. Your eMagiz services can be unavailable for up to four minutes.

Features:
1) Auto healing for EFS locking
2) Auto healing for coordination failed
3) Auto healing out of memory
4) eMagiz runtime 5.0.3

Bug fixes:
1) Fix for log groups preventing a re-install of a runtime
