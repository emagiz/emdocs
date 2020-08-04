### User Guide Unit Testing eMagiz

Below the user guide for Unit Testing. In this guide we will focus on the following parts:
-	Adding Test Messages
-	Creating a unit test
-	Executing a unit test
-	Validate results of unit test

Should you have any questions, please contact productmanagement@emagiz.com.

Last update: July 24th 2020

## Pre-requisites
- Basic knowledge of the eMagiz platform
- Understanding of Unit testing concept
- On- or offramp (without splitter or router) that needs to be tested

## Introduction

The eMagiz platform gives the user the option to test certain flows via the unit test functionality embedded in the platform. With the help of this functionality you can more easily develop and thoroughly test functionality that is build in these flow as ever before. Making use of this functionality consists of the following four steps:
1.	Adding Test Messages
2.	Creating a unit test
3.	Executing a unit test
4.	Validate results of unit test

## Adding Test messages
The first step would be to add a test message. Ideally these messages are known in advance and part of the Discovery. In eMagiz there is a centralized place where you store all relevant files and data belonging to an integration and that is Capture. 
For adding test messages this is the same. In Capture you have the tab called Message Content. In this tab you have the option to navigate to Test messages.

<p align="center"><img src="../../img/howto/unittest-image1.png"></p>

In this view you have the option to Create a new message, Edit an existing message or Delete a message. When pressing Create or Edit you end up in the following screen

<p align="center"><img src="../../img/howto/unittest-image2.png"></p>

In here you enter or change a Name for your message and the payload of the message resulting in something like this. After pressing save you have stored your test message which can be used in a unit test. Be aware, the name is crucial as all test messages are shown when you want to select one as input or output of your integration. Discuss a proper naming convention amongst those with whom you develop.

<p align="center"><img src="../../img/howto/unittest-image3.png"></p>

## Creating a unit test
On flow level in eMagiz you can create a unit test that is specific for that flow. This can be done by pressing the Configure tests button located on the bottom of your screen. For making a unit test the editing modus on the flow is not mandatory.
Pressing this button leads to the following screen. In the left hand side panel you see all test messages that are coupled to integrations in Capture. Therefore it is wise to name your messages accordingly.

<p align="center"><img src="../../img/howto/unittest-image4.png"></p>

First step in creating a unit test is to link messages to the components in the flow that have a orange icon with a exclamation mark linked to them. This action is mandatory for the inbound and optional for the outbound adapter(s).
So lets first link a message to only the inbound adapter. This can be done by opening up the list on the left side, selecting the correct message and dragging it onto the inbound adapter. If you were successful the icon should have disappeared as is shown below.

<p align="center"><img src="../../img/howto/unittest-image5.png"></p>

If you have an expected outcome in case of success (message reaches the last component of your flow in the structure as expected) and/or in case of failure (messages goes wrong somewhere) you could also link these to their respective components.
Next step is to press the Add test button, Press Edit and select the correct Input message. 

<p align="center"><img src="../../img/howto/unittest-image6.png"></p>

After you have selected the correct message press Done and give the Unit Test a name (by pressing the pencil icon)

<p align="center"><img src="../../img/howto/unittest-image7.png"></p>

Congratulations, you have successfully create a unit test!

## Executing a unit test
You can simple execute a unit test by pressing the Run test button. After this eMagiz will show you the following popup. In case properties are used in the flow you are about to test you need to add values for them. If not just press Run Test (Note: When you are the first of the day using the functionality the Unit Testing bus needs to wake up. Therefore it can take a while until you get a result)

<p align="center"><img src="../../img/howto/unittest-image8.png"></p>

When no popup indicating an error shows up the test has run successfully. Congratulation! The color of the backscreen indicates the result of the test. For more information on validating the result please see the section on Validate result of unit test.
Validate result of unit test
After you ran the test eMagiz gives you, the user, feedback in two ways:
1.	The color of the background of the screen (red means failed, green means success)
2.	Showing the state of the message in each component it passes
Let’s look into these two ways with a little bit more detail

## Feedback through color of background
As specified before the color of the background is a quick indicator to the user telling the user if the executed test was successful or not. If the background turns red it means the test was not successful. Be aware, when you do not define an expected outcome the result of the test will always be failed and therefore the color will also be red. For an example see below

<p align="center"><img src="../../img/howto/unittest-image9.png"></p>

After you have specified the expected outcome of the flow the screen will turn green if the actual result equals (in every detail) the expected outcome. If the actual message does not match the expected outcome the background will turn red. See below for a green result!

<p align="center"><img src="../../img/howto/unittest-image10.png"></p>

## State of message throughout the flow
eMagiz will also give you feedback on how the message looks like in every component of the flow it passed. This way you can validate if certain headers are set correctly and if certain transformations were successful. Below is an example of comparing the input and output of the transformation component shown in the flow. In here you can see in detail what the transformation has done. This way you can determine whether the change you have just made was indeed successful.

<p align="center"><img src="../../img/howto/unittest-image11.png"></p>

Now you have successfully learned how to implement a unit test within eMagiz and test it you can develop more effectively and more robust.
