Release notes for cloud slot template R13 template
Service affecting final template to use the R13 single lane release. This is the second of two steps for your upgrade to the new R13 template.

Note: You have to apply this final template immediately after the intermediate template is finished to restore services.

Process:
To use the new R13 release of our cloud template we upgrade in two steps.

Final step:
2) Use this final template (restoring services) (duration: 4 minutes)
- This step will recreate all the machines in your cloudslot 
- The runtimes on the machines will be restored using the active release in the eMagiz portal
   
User actions after applying the final template:
- Check if all runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
- Check if messages pass through the bus by verifying a critical message flow in external systems

Features R13 release:
1) Fixed the resource limit error on cloudformation deployment (for very large cloud slots)