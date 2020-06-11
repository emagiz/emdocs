Controlling the eMagiz Cloud

Issue date: 26-05-2020

This document discusses how you can control and execute various actions via the eMagiz portal on the eMagiz cloud. The main idea of having the ability to control the eMagiz Cloud from the portal is to increase what a user can do without any the help of experts that master the specific Cloud environment where the eMagiz instance is deployed (in this case AWS). This functionality enables users to make the following configuration changes to the eMagiz Cloud - currently only the first step is described (rest will follow shortly).
- Upgrade Cloud Template
- Add / Remove Runtimes
- Add / Update Routes
- Add / Update Certificates
- Start / Stop Runtimes
- Start / Stop Machines
- Reset Runtime
- Clean Store
- Slot Standby / Slot wakeup
- Mendix stand by connector

In this document we will discuss each of these actions separately to make it even easier for you, the use, to control the eMagiz Cloud.
To summarize, controlling the eMagiz Cloud gives you:
-	Tools to stay in control of the eMagiz Cloud.
-	A way to do it yourself.



## Best practices
-	Read the release notes on the eMagiz portal every time a new cloud template is released by eMagiz. These release notes can be found under Documentation -> Release Notes -> Cloud Templates
-	Keep your Cloud setup as updated as possible
-	When using the Slot Standby / Slot Wakeup functionality combine this with the Mendix stand by connector to prevent a large number of errors / warnings in the log 
-	All actions described below can only be executed on AWS cloud environments and AWS cloud runtimes for now
-	If you are unsure what an action does, please discuss the steps you want to make with someone else before executing them. Contact productmanagement@emagiz.com or use the Q&A section in the eMagiz Portal
-	All changes made from the eMagiz Portal are only send to the AWS cloud at the moment you press the Apply to Environment button. If you do not press this button, your changes only reside in the eMagiz Portal (Integration model) and not in the cloud.
-	In case of a so-called double lane bus (failover available) you have the option to first update the failover setup (Availibility Zone B) and at a later stage the ‘live’ setup (Availability Zone A). This to prevent down-time of the platform instance

## How-to steps Upgrade Cloud Template
Follow these steps carefully in order to acquire the desired result. Before we explain step by step which actions to take to upgrade a cloud template let us first consider why you want to update a cloud template in the first place. 
 
A Cloud template is the configuration, specified by eMagiz, how deploy Architecture will run in AWS and which supporting tools (such as auto healing, auto recovery and improved alerting for instance) are available for your environment. With each new cloud template these functionalities will improve autonomous use and stability of the instance. Which changes exactly are made in a particular cloud template can be found in the Release notes section under Community -> Documentation in the eMagiz portal. 

What is important to understand is that the update of a Cloud template can be done without any downtime in case your particular environment runs in a failover scenario. You can simply update zone A and zone B in sequence so that all services can continue to work without interruption. In case you run in a single lane scenario, you will have to plan a short downtime of the environment to perform the update which takes between 1 or 4 minutes. There will be no loss of messages.

Below the steps to update a Cloud template automatically or at the moment the pop-up appears. 
0. Please switch off Root Monitoring off before proceeding. 
1.	Navigate to Deploy -> Architecture for the bus you want to perform this action
2.	If a new template has been made available you will see a popup screen asking if you want to update to the latest cloud template. If this fits you can execute the upgrade of the cloud template by pressing the green button at the bottom of the popup. If you however which to delay it you can silence the pop up for a day by pressing the other button. Another option (manually) to update your cloud template can be found starting at step 5
3.	By pressing the button in step 2 eMagiz will now automatically update the cloud template for you. You can follow the progress of this update by right clicking on the white part of the canvas and selecting details you will see the cloud template number and the state of the last update. See figure below. If it says update complete the update has been successful. 
4.	Execute all standard checks, i.e checking the logs under Manage -> Log Entries and verify if you can access the runtimes via runtime dashboard
5. Switch root monitoring on.

In case you decide to run the update the later, here are the steps to perform this update manually.
0.  Switch root monitoring off.
1.	Select the correct environment for which you want to perform this action. 
2.	Press Start Editing button. Located on the left bottom of the screen
3.	Right click on the white canvas and select details
4.	Select the cloud template of your choosing in the dropdown. Be aware, eMagiz will only let you choose the next GA version apart from your current version.
5.	Don’t forget to press Apply to environment on the left bottom of the screen to make sure that your changes are applied to the AWS cloud
6.	Verify if the update has been successful. This can be seen in the details screen by looking at the Last known state
7.	Execute all standard checks, i.e checking the logs under Manage -> Log Entries and verify if you can access the runtimes via runtime dashboard
8.  Switch root monitoring on.

