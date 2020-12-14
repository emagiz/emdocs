## Life Cycle Management in eMagiz - Cross check complete Integration Model

This document discusses the practical implementation of Life Cycle Management within eMagiz.
The main idea behind Life Cycle Management in general and in eMagiz is to stay in control of the integration landscape we are developing alongside our customers. Life Cycle Management does not only entail deleting flows and information when a certain integration has reached its end of life but also keeping your integration landscape up to date with new features and developments as made by the eMagiz product development team.
Life Cycle Management should be a conscious part of everyday life for everyone that plays a part within a team, project or program. This way the team, and not the individual, will add the most value to the process.

To summarize, life cycle management gives you:
-	Tools to stay in control of your integration landscape.
-	A way to keep up to date with the latest developments within the eMagiz portal.
-	Everyone should be involved


## Best Practices
-	Remove flows   as part of completing your production deployment (after a grace period in which you conform that everything works as expected). This to avoid a backlog of delete actions. A standard grace period would be two weeks. One could deviate from this standard if they have discussed this with the business owner.
-	Remove flows only after a written approval of the business owner of the process
-	Remove flows from back to front. In other words, start in Manage and end in Capture.
-	Regularly update your flows in Test and Acceptance so you can test new functionality released by eMagiz
-	Updating flows to the latest build numbers can be done in two ways
•	Deploy with each production deployment a certain number of extra flows for which nothing has changed but the build number
•	Use a separate deployment moment to upgrade all flows, without functional changes, to the newest build number


## How to implement life cycle management
This chapter will discuss a step to step guideline of how to implement Life Cycle Management within the context of eMagiz.

Follow these steps carefully in order to acquire the desired result. If a step is unclear or you are not able to follow it, please contact CAPE Academy. Steps 1 through 7 outlined below need to be executed separately on Test, Acceptance and Production

### Removal of flows
1.	Identify the flow in question you want to remove. Be aware that the removal of a flow is done in pairs. You cannot delete an onramp without deleting the entry. Obviously the same applies to the offramp and exit combination
2.	When you have identified the flow you want to delete navigate to Manage -> Alerting
3.	Within this Tab navigate to Triggers (look at the Tag name when following these instructions)
	-	If you have configured the alerting following the best practice outlined in the user guide for Alerting, the following triggers (at least!!!) need to be changed. For your specific situation more triggers could be relevant
		- Standard – Queue consumers too high
		- Standard – Queue consumers too low
	- If you are removing the last flow belonging to a system and you have followed the best practice outlined here the following triggers (at least!!!) need to be changed. For your specific situation more triggers could be relevant
		- Standard – Data measurements missing
		- Standard – Log entries missing
		- Standard – Error log entry
4.	After you have removed the flow, and possibly runtime, from all relevant triggers you navigate to Deploy -> Releases
5.	In this page you create a new release (naming it according to the naming conventions) in which you remove the flow you want to remove from your integration landscape.
6.	Deploy this release to the environment(s) you already have executed step 1 through 5 for. It is advisable to leave a grace period between removing things from Test before removing them from Production just to be sure.
7.	Navigate to Deploy -> Properties and press the Find Unused button. The result of this action will show you all unused properties within your active release. Identify the ones related to the flow you want to throw away and delete them if they are only used there.
8.	After executing step 1 through 7 for all environments that are relevant for you (Test, Acceptance and Production), and only after executing all these steps you can continue with step 9
9.	Navigate to Create -> Add Integrations
10.	Select the flow you want to throw away in Create and press Save Selection

### Removal of resources
11.	Navigate to Create -> Resources
12.	Select all resources that don’t have any link to any flow. This can be seen by looking at the Configuration(s) column. If this does not show any flow, the resource is not used anymore. If life cycle management has been applied correctly before only custom resources linked to the flow, and only to that flow, you have deleted in Step 9 and 10 should be shown. Be aware, eMagiz automatically deletes the validation and transformation if they are build via the eMagiz tooling.
13.	Navigate to Design -> System Message
14.	Clear the System message (if it exists)
15.	Navigate to Capture
16.	Click on the message type you want to remove. If this message type only occurs once you can continue with step 17. You can determine whether a message type only occurs once by clicking on the message type. This way it will show you were the message type in question is used. If not continue with step 20

### Removal of unused CDM elements
17.	Navigate to Design -> CDM
18.	Select the Message type you are currently deleting. This to see the CDM message you are working with.
19.	Check for each attribute within this CDM message of this attribute is not used anymore in any other CDM message. Repeat this step for each attribute, entity and relationship that exists within the system message.
a.	If the answer is yes, delete the attribute
b.	If the answer is no, leave the attribute in the CDM.

### Removal of message types & Systems
20.	Navigate to Capture
21.	Right click on the message type you want to remove and select Delete integration. If no integrations are connected to the system anymore you can delete the system by right clicking on the system and pressing Delete system. 

### Transfer settings from Design to Create (Optional, only relevant in fringe cases)
22. There are fringe case where it could be that you, for example, have changed the number of runtimes of a specific system after this system has been moved to Create. 
If you have done so you can synchronize Design and Create afterwards by navigating to Create -> Settings and selecting the tab called Transfer settings from Design.
23. Under this tab there is the option to select Multi-runtime connectors. Search for the runtime you are trying to clean up.
24. Select the runtime and press Transfer nr of runtimes. This will make sure that all ILM phases are synced up in terms of how many runtimes belong to a system.

When you have done this the last step is to remove the runtime from the runtime dashboard. This can be done by any eMagiz administrator (productmanagement@emagiz.com). 
This also provides an extra check that you have followed this how to correctly. If you have missed something they will let you know.

