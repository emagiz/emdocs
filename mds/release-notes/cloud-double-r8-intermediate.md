Release notes for cloud slot template R8 intermediate template
Non-service affecting intermediate template to go to the R8 double lane release. This is the first of two steps for your upgrade to the new R8 template.

To use the new R8 release of our cloud template we upgrade in two steps, with only the second step being service affecting.
Steps:
1) Use the intermediate template (non service affecting)(duration: 4 minutes)
User actions after applying the intermediate template:
- Check if all ".02" runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
2) Use the final R8 template (service affecting)(duration: 4 minutes)
User actions after applying the final template:
- Check if all ".01" runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
- Check if messages pass through the bus by verifying a critical message flow in external systems

By selecting this template and pressing 'update AWS' we will update all zone B machines. Your service will not be affected, but during this update failover is unavailable for up to four minutes.

Features:
1) Auto healing Instance Recovery on AWS system failure
2) Auto healing port check
3) Auto healing for out-of-memory situations
4) Auto healing for coordination failed
5) Improved notification email to customer support when auto healing is triggered
6) New logging facility for customer support to better monitor machine health
7) Instances now have functional hostnames
8) Java runtime environment is updated to OpenJdk 8u2228(AdoptOpenJDK, 8u222-b10, HotSpot)
9) Fixed the resource limit error on cloudformation deployment