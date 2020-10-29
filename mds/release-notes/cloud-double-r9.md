Release notes for cloud slot template R9 template
Service affecting final template to use the R9 double lane release. This is the second of two steps for your upgrade to the new R9 template.

Note: You have to apply this final template immediately after the intermediate template is finished to restore services.

Process:
To use the new R9 release of our cloud template we upgrade in two steps.

Final step:
1) Use this final template (restoring services) (duration: 4 minutes)
- This step will recreate all the machines in your cloudslot 
- The runtimes on the machines will be restored using the active release in the eMagiz portal
   
User actions after applying the final template:
- Check if all runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
- Check if messages pass through the bus by verifying a critical message flow in external systems

Features R8 release:
1) Auto healing Instance Recovery on AWS system failure
2) Auto healing port check
3) Auto healing for out-of-memory situations
4) Auto healing for coordination failed
5) Improved notification email to customer support when auto healing is triggered
6) New logging facility for customer support to better monitor machine health
7) Instances now have functional hostnames
8) Java runtime environment is updated to OpenJdk 8u222 (AdoptOpenJDK, 8u222-b10, HotSpot)

Features R9 release:
1) Fixed the resource limit error on cloudformation deployment (for very large cloud slots)