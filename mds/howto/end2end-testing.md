This document describes best practices on how to set-up an end-to-end test. End-to-end testing is a technique used to test whether the integration is behaving as expected from start to finish. There are various ways to mimic a Production like situation which means that these test do not involve any test applications as Postman or SoapUI. The objective of the performance test is to verify that your solution not only works for a handful of messages but also when thousands and thousands of messages are sent.

## Introduction – Why end-to-end testing?
The purpose of performing end-to-end testing is to identify system dependencies and to ensure that the data integrity is maintained between various system components and systems. This means that each change made to an integration should be tested to make sure that production-like scenarios don’t lead to any unexpected errors when the new functionality is released to production. 
During the development of new features, you will need multiple testing methods. Each method has a different purpose to help you in the different steps of thsee development process. Not in every case each test is applicable however they are still recommended. Examples include:
-	Unit testing
	- Offline testing
	- Flow testing
	- Integration testing
-	Regression testing
-	Performance testing
-	End-to-end testing (UAT)

An important step is to determine as early as possible the different scenarios which you need to test during your end-to-end test. The earlier you have these clear, the better you are able to test your changes during the process. This will improve the quality of the integration. Before starting the Create phase, the test scenario’s need to be agreed upon with the business owners. This is one of the Definition of Done items from the Discovery (Capture & Design) phase.
During the development, you have considered what the steps and effects are of the new functionality and change. While implementing, you need to test continuously  to verify if the changes made behave as expected. The eMagiz platform offers you features which help you during these tests. If you need to change transformations or need to create a XPath, you can use the unit testing feature in eMagiz. If this is not applicable in your case, use several tools which are not in eMagiz to help you develop. These tools will give feedback on your changes meaning that you can easily update your change or test with multiple scenarios by varying the input message. You can do this before you start editing in eMagiz. Example of these tools are XSLT Fiddle, Freeformatter Xpath Tester, IntelliJ, and Notepad++.
After implementation in the flow, you can use the Unit Test feature to test whether every component and eventually the whole flow works. You can repeat these steps for each Onramp and Offramp flow that needs to be adjusted. 

More information about the Unit Test feature and how to use it can be found in the eMagiz portal in Academy: Community -> Academy -> eMagiz ABL Block 1 -> Unit Testing in eMagiz. 

In Entry- and Exit Connectors you could use the Debugger in combination with the Deploy feature during editing the Entry or Exit Connector. Based on the debugger results, changes can be made directly and directly tested again with the same cycle. For Entry and Exit Connectors, the Unit Test feature is expected in the Product roadmap.
When all flows are ready, the whole integration needs to be tested, this is called the integration test. This is a technical test to make sure that the integration is technically sound. Ideally, you test the integration from application to application. If you do not have access to system A, you could use one of the following options (based on connectivity with system A) to send messages to system B:
-	SOAP UI
-	Postman
-	Placing files in a certain location and let eMagiz pick up these files

If the integration works as expected, you have to verify whether your changes might affect other flows. If they don’t have any functional changes, execute a regression test to make sure that the integration still behaves as before you implemented the new functionality in the other flow. Regression testing is re-running functional and non-functional tests to ensure that previously developed and tested software still performs after a change. If you don’t do this, you might see unexpected results in the production environment.
To ensure that not only functionally the integration works properly, but also when a lot of messages are processed, you can perform a performance test. The objective is to mimic a Production like situation. This to verify that your solution not only works for a handful of messages but also when thousands and thousands of messages are sent.
In this how-to, we will focus on end-to-end testing. This is the final functional test with end users to test production-like scenarios with production-like data. The goal is to get the business’s approval. The document discusses the preparations before the end-to-end test, how to perform the test and what the next steps are till the production deployment.

## Step 1 – Preparations 
You would like to perform the final end-to-end test as early as possible when you have completed developing. Therefore, it is important to plan out this test as soon as you start developing to keep the developing cycle as short as possible. 
Ideally, you have agreed the test scenarios with the business before the development. These test scenarios are used during the end-to-end test to conclude whether the new functionality works. To prepare your test, please consider the following:

Before development:
-	Plan the end-to-end test with the stakeholders
-	Agree upon test scenarios
-	Check whether test data is available in the testable environment to test all your scenarios
-	If not available, create the data or ask the business to create the test data

Before end-to-end test:
-	Check whether data is available which you want to use in your test.
-	If not available, create the data or ask the business to create the test data.
-	Re-test the integration on the environment which you use to do the end-to-end test to confirm that everything works. Use other test data than you would like to use or have used in your end-to-end test. 
-	It is important that you always test the integration system to system. Avoid using applications as Postman or SOAP-UI to simulate one of the applications. Using such applications does not simulate the process on the live environment and is less reliable. 

## Step 2 – The end-to-end-test
During the end-to-end test, many things can happen or go wrong. It is important to keep the scope of your change or story in mind while doing the end-to-end test. The following guidelines can help you during your test:
-	Before testing, inform the stakeholders what the scope is of the change and what the agreed test scenarios are. This will help you and the stakeholders remember the scope of the test. Stakeholders often have the tendency to discuss other features or issues during a test session.
-	Talk the stakeholders through the changes and how the integration works (differently). This will increase the understanding of the business. Keep in mind your audience, not everyone is interested in the technical details. 
-	Let the business perform the test scenarios as agreed. 
-	Write down feedback if issues or other suggestions occur. 
-	At the end of the test session, discuss the feedback and other suggestions and plan a new end-to-end test. 
-	If everything works as it should and the stakeholders approve, the process starts to deploy the changes to the live environment. An example of such a process is: you will sent an email requesting confirmation that everything works as intended. The approval via email is required to perform next steps.

Although changes are made for an existing or new flow, you might need to update your deployment plan. The usage of the deployment plan also structures the deployment for you. It ensures that all the flows are deployed which are in the releases and ensures that all your changes are deployed. Apply these changes not only for the production environment but also for your acceptance and test environment. To verify you applied these changes correctly, do not forget to test the new deployment plan.  

## Step 3 – Make it production-ready
After receiving the approval, you can make the change production-ready. This is the moment that you will hand the deployment over to the person who will perform the production deployment. Make sure to send all the required information for a smooth deployment. In larger projects it is often the case that only a few people have the rights to perform a production deployment. 
As developer, you can help your team by handing over all the information required for the deployment. This includes information such as:
-	Adjusted flows with flow numbers
-	Dependencies
-	New/Changed properties with their (new) value
-	Business approval

Structuring the information may help your team, think about a structured Go-Live document which all team members use for every story for example.
Even if you perform the deployment yourself, structuring this information is extremely helpful. It reduces errors during the deployment phase if you split the preparations and eventually the deployment itself. Also, a Go-Live document might help you when business requests information about the deployment if it causes issues. Since it provides you and the business with all the information related to the deployment. Update (if applicable) and use the deployment plan to perform the deployment. 
After deploying, always inform the business that the change is available on the live environment. Please always check if the changes produce no issues and check this also with the business. If you see issues, consider a rollback or a hotfix.
