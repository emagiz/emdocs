## Identification Legacy parts

Below you will find several sections that identify parts of the framework that are deemed legacy and are replaced by newer and better alternatives. The guide is split up per legacy part. Per section we describe the legacy method, the new method and how to migrate from legacy to new. Should you have any questions, please contact productmanagement@emagiz.com.
Last update: August 8th 2020


## Pre-requisites
- Basic knowledge of the eMagiz platform



## Old Transformation Tooling
A key feature of eMagiz always has been the manner in which you can visually see what you need to transform from A to B. At a certain point eMagiz provided a new way of Designing the transformation. This meant two things. The Design phase in eMagiz has now become the place to set up your transformations instead of doing everything in Create. This way your process of developing an integration became more intuitive and less complex.


### Legacy
You can identify Legacy resources (transformation or validation) by navigating to Create -> Resources. In here you can search for XML definition (classic) or XML transformation (classic). All results given back mean that these resources are created with the old transformation tooling and need to be migrated if the resource in question is still being used in a flow. You can see whether they are still used by looking at the configuration column.

<p align="center"><img src="../../img/howto/userguide-legacy-1.png"></p>

Opening a definition in the old tooling will look like this

<p align="center"><img src="../../img/howto/userguide-legacy-2.png"></p>

### New
You can identify New resources (transformation or validation) by navigating to Create -> Resources. In here you can search for Message Definition or Message Transformation. All results given back mean that these resources are created with the new transformation tooling. These resources don’t need to be migrated. You can see whether they are still used by looking at the configuration column. If not used you can remove, after verifying if they are indeed not used anymore, these resources as part of your lifecycle management process.

<p align="center"><img src="../../img/howto/userguide-legacy-3.png"></p>

Opening a definition in the new tooling will look something like this

<p align="center"><img src="../../img/howto/userguide-legacy-4.png"></p>

### Migration
Migrating from the old tooling to the new tooling takes several steps to make it work correctly. Below you will find all these steps. Follow them carefully to achieve the desired result
1.	Download the XSD, from Create -> Resources, of the system message for the flow you want to migrate
2.	Download the XSD, from Create -> Resources, of the CDM message for the flow you want to migrate
3.	Download the XSLT, from Create -> Resources, of the transformation between the system message and CDM
4.	Navigate to Design
5.	Open the CDM
6.	Open the XSD of the CDM message to see how the CDM message looks
7.	Verify if the entities and attributes in your CDM message are already available in the CDM that you have currently open
-	If yes, continue with step 9
-	If no, continue with step 8
8.	Add the missing entities and attributes to your CDM that are needed in your CDM message
9.	Open the message type of the flow for which you want to migrate
10.	Construct the CDM message based on the XSD you downloaded in step 2
At this point you have successfully migrated your CDM XSD to the new transformation tooling
11.	Navigate to Capture
12.	Open the information page for the flow for which you want to migrate
13.	Add the XSD that you downloaded in step 1 as XSD to Message Content
14.	Navigate to Design
15.	Open the system message page for the flow for which you want to migrate
16.	Press the import button and select From Capture
17.	Select the XSD you have added to Capture in Step 13
Congratulations, at this point you have successfully migrated your system message to the new transformation tooling
18.	Navigate to the message mapping page.
19.	Draw the lines between system message and CDM (or vice versa) based on the XSLT you downloaded in step 3. Based on the color of the background you can see which part of the screen is CDM (green) and system message (blue)
Now you have successfully transformed the XSLT into the Message Mapping in Design
20.	Navigate to Create
21.	Open the flow for which you want to migrate
22.	Open the tabs System message, CDM message and Transformation one by one to verify if the results of the previous steps in Design are visible in Create.
23.	Press Start Editing
24.	Navigate to Resources
25.	Press Add bus resources to flow
26.	Search for the correct resources and add them to the flow
-	In a onramp you need the system message validation and the transformation from system to CDM
-	In a offramp you need the CDM message validation and the transformation from CDM to system
27.	Link the resources to their respective components in the flow
After this you have successfully linked the new transformation tooling resources to your flow in Create
28.	Verify based on the XSLT downloaded in step 3 if changes have to be made to the transformation made in step 19. This can de done by comparing the old and new XSLT. The new XSLT can be downloaded via the Resources tab of the flow
-	If no changes are necessary, continue with step 30
-	If changes are necessary, continue with step 29
29.	Recreate the old mapping logic via the Transformation page in the flow. This can be done in various ways
-	Filter
-	Transformation
-	Static Input
-	Aggregation
-	Grouping
Now you have migrated from the old to the new tooling. Last step will be to verify everything works exactly the same as before. This can be done in two ways
30.	Test your changes
-	If possible, test your flowing by using the Unit Test functionality. For more information see [User Guide Unit testing](userguide-unitttest.md)
-	Otherwise test it by deploying the flow and sending a message.
31.	Verify your results
-	If the result is the same you are finished
-	If changes exists, analyze them and make changes to the transformation until you have reached the correct result
Congratulation, you have successfully migrated your flow from the old transformation tooling to the new transformation tooling.

## Error handling synchronous flows

To properly manage an eMagiz project you need to have robust and stable error handling. This process of error handling was the same for both asynchronous and synchronous flows. In this process all errors that were thrown by a flow would be routed via the asynchronous error process each eMagiz project has. For synchronous flows this meant that apart from the actual error each step in the process that did not receive a message within the set timeframe would subsequently throw an timeout error.
This process had three disadvantages
-	The client needed to wait for the allowed timeout period (default 20000 ms) before knowing whether or not the action succeeded
-	The client only received a generic timeout error instead of information on the error that occurred downstream
-	Any synchronous error could lead to up to five separate error messages making it more confusing and difficult to properly analyze what was going wrong
Based on these consideration the way errors are handled in a synchronous flow has changed. See below for the old way, the new way and how to migrate to the new way

### Legacy

In the legacy situation the flow would handle its error message asynchronously. See a picture below for how this is configured in the flow. That way the other flows in the chain are still waiting for an answer that will never come.
<p align="center"><img src="../../img/howto/userguide-legacy-5.png"></p>

### New

In the new situation all (error) messages are given back to the flow preceding the current flow. This way the error message is given back to the client so they know what went wrong. This looks as follows in a flow
<p align="center"><img src="../../img/howto/userguide-legacy-6.png"></p>

### Migration

Migrating from the old way of handling errors in a synchronous flow to the new way of handling errors in a synchronous flow takes several steps to make it work correctly. Below you will find all these steps. Follow them carefully to achieve the desired result
1.	Identify the synchronous flow in your eMagiz project that you want to change
2.	Navigate to Create and open the exit
3.	Loop back the error to the response channel. See below for the correct configuration
<p align="center"><img src="../../img/howto/userguide-legacy-7.png"></p>

4.	Save the flow and go to the offramp
5.	Loop back the error to the response channel (see above for the correct configuration)
6.	Add a standard filter component and fill it in according to the below specifications
<p align="center"><img src="../../img/howto/userguide-legacy-8.png"></p>

7.	Add a new channel and link the components to achieve a result as shown above under the new section
8.	Save the flow
9.	Repeat steps 5,6 7 and 8 for the onramp
10.	Open the entry
11.	In here you have the choice to handle the error in two ways
-	Send the error back to the client. This can be achieved by following steps 5,6,7 and 8
-	Send the error to the client after setting the statusCode and the error message. For this continue with step 12
-	Don’t send the error to the client but to the emagiz error flow instead. For this continue with step 13
12.	To specify what the client will see as a response in case of an error you can change the following two things
-	The statusCode (i.e. 401,403,500,501). This can be done by setting the header, with the help of a standard header enricher, titled http_statusCode to the desired statusCode
-	The payload. The payload can be changed to what you want with the help of a standard transformer or an XSLT transformer. An example of this is shown below
<p align="center"><img src="../../img/howto/userguide-legacy-9.png"></p>

13.	Add a JMS outbound channel adapter and send the messages to the eMagiz error flow of your project. This way the message will show up in the Error messages overview of eMagiz but all timeout errors won’t show up anymore. 
14.	Test your changes
-	If possible, test your flowing by using the Unit Test functionality. For more information see [User Guide Unit testing](userguide-unitttest.md)
-	Otherwise test it by deploying the flow and sending a message.
15.	Verify your results
-	If the result is the same you are finished
-	If changes exists, analyze them and make changes to the transformation until you have reached the correct result

Of course it is possible to use a combination of the suggestion made in step 11, 12 and 13 to configure the error handling to your specific use case. If you are planning on implementing a new synchronous flow please consider the API Gateway functionality. For more information please see [ User Guide API Gateway](userguide-apigateway.md)

Congratulations, you have successfully migrated the error handling of your synchronous flows to the new best practice

## Error flow

The error flow is part of the default in any eMagiz project. This flow handles all errors that are thrown by (a)synchronous flows within your project and passes them through to the iPaaS so they show up under Manage -> Error Messages. Recently we have made some changes to make the error flow work even more optimal.

### Legacy

In the legacy situation the flow would determine for each message whether or not message tracking was enabled. Based on that the error handling responded in a slightly different manner.
<p align="center"><img src="../../img/howto/userguide-legacy-10.png"></p>

### New

In the new situation the flow treats all messages the same and removes all headers to reduce the chance the error message will cause problems downstream for the iPaaS or the portal.
<p align="center"><img src="../../img/howto/userguide-legacy-11.png"></p>

### Migration

Migrating from the old error flow to the new error flow takes several steps to make it work correctly. Below you will find all these steps. Follow them carefully to achieve the desired result.
1.	Determine if you made any custom changes to the error handling
-	If not, continue with step 2
-	If yet, continue with step 6
2.	Navigate to Create
3.	Right click on the Error process and press Reset flow
4.	Test the flow
5.	Verify your results
-	If the result is the same you are finished
-	If changes exists, analyze them and make changes where necessary
Congratulations, you have successfully migrated the error flow to the new setup
6.	Determine if these changes are still justified
-	If no, execute steps 2, 3, 4 and 5
-	If yes, continue with step 6
7.	Write down all manually changes you still need
8.	Navigate to Create
9.	Right click on the Error process and press Reset flow
10.	Add the manual changes back to the flow
11.	Test the flow
12.	Verify your results
-	If the result is the same you are finished
-	If changes exists, analyze them and make changes where necessary
Congratulations, you have successfully migrated the error flow to the new setup
