Release notes for cloud slot template R8 template
Service affecting final template to use the R8 double lane release. This is the second of two steps for your upgrade to the new R8 template.

Process:
To use the new R8 release of our cloud template we upgrade in two steps, with only the second step being service affecting. Below are the remaining steps.
Steps:
2) Use the final R8 template (service affecting)(duration: 4 minutes)
User actions after applying the final template:
- Check if all ".01" runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
- Check if messages pass through the bus by verifying a critical message flow in external systems

By selecting this template and pressing 'update AWS' we will update all zone A machines. Your service will be affected for a short time.

Features:
1) Auto healing Instance Recovery on AWS system failure
2) Auto healing port check
3) Auto healing for out-of-memory situations
4) Auto healing for coordination failed
5) Improved notification email to customer support when auto healing is triggered
6) New logging facility for customer support to better monitor machine health
7) Instances now have functional hostnames
8) Java runtime environment is updated to OpenJdk 8u222 (AdoptOpenJDK, 8u222-b10, HotSpot)
9) Fixed the resource limit error on cloudformation deployment