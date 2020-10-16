Release notes for cloud slot template R14 template
Service affecting template to use the R14 single lane release. This is the only step for your upgrade to the new R14 template.

Process:
To use the new R14 release of our cloud template we upgrade in two steps.

First step:
1) Use this template (replace instances) (duration: 4 minutes)
- This step will replace all the machines in your cloudslot 
- The runtimes on the machines will be restored using the active release in the eMagiz portal
   
User actions after applying the final template:
- Check if all runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
- Check if messages pass through the bus by verifying a critical message flow in external systems

Features R14 release:
1) Fixed double sending of runtime logs to cloudwatch which could trigger repeating auto healing actions.