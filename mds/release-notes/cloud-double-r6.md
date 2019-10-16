Service affecting final template to use the R6 double lane release. This is the second of two steps for your upgrade to the new R6 template.

Process:
To use the new R6 release of our cloud template we upgrade in two steps, with only the second step being service affecting. Below are the remaining steps.
Steps:
2) Use the final R6 template (service affecting)(duration: 4 minutes)
User actions after applying the final template:
- Check if all ".01" runtimes are reachable by the runtime dashboard
- Check if all flows have been installed according to the active release
- Check if messages pass through the bus by verifying a critical message flow in external systems

By selecting this template and pressing 'update AWS' we will update all zone A machines. Your service will be affected for a short time.


Features:
1) Auto healing for EFS locking
2) eMagiz runtime 5.0.3

Bug fixes:
1) Fix for log groups preventing a re-install of a runtime
