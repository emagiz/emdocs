<div class="ez-academy">
	<div class="ez-academy__body">
		<main class="micro-learning">
		<ul class="doc-nav">
			<li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-testing-in-emagiz" class="doc-nav__link">Home</a></li>
			<li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
			<li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
			<li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
			<li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
		</ul>

<div class="doc">

##### Intro

# System Integration Testing

In this microlearning, we will focus on system integration testing. At some point in time you have build your solution and have tested your single unit/flow to see whether or not it works. A logical next step would be to link certain units/flows together to test whether you can communicate via eMagiz between two separate systems. A crucial part of a system integration test is that both the sending and receiving system are online and ready to produce or consume.

Should you have any questions, please contact academy@emagiz.com.

- Last update: April 8th 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Understanding of the flow testing functionality

## 2. Key concepts
This microlearning centers around system integration testing.

By system integration testing we mean: A test that is designed to test whether two systems can communicate via eMagiz in the intented way

Auditing the eMagiz data models can be done by navigating to the specific data model in question in the Design phase and selecting the button called History located in the bottom bar.

##### Theory
  
## 3. System Integration Testing

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
During the development, you have considered what the steps and effects are of the new functionality and change. While implementing, you need to test continuously  to verify if the changes made behave as expected. The eMagiz platform offers you features which help you during these tests. While doing development you can use the flow testing functionality in eMagiz to test your small units/flows.

However at some point you need to link these units/flows together. That is when you as a developer should want to do a system integration testing to determine for yourselves that everything that you and others within the team have worked to connect two systems together 


Knowing how changed what at the eMagiz Data model level is crucial for proper control and management of these data models.

If you want to audit any of these eMagiz data models (look at the history of changes made to the data model by whom) you can navigate to the Design phase of your project and open the specific data model.
In the view that you will be presented with you will see a button on the bottom bar called History.

The conceptual idea will be explained in this microlearning with the help of the CDM (the eMagiz data model for messaging). The same idea applies to the other eMagiz data models available.

If you want to audit the CDM (look at the history of changes made to the CDM by whom) you can navigate to the Design phase of your project and open the CDM. 
In this CDM view, you have a button on the bottom bar called History.

<p align="center"><img src="../../img/microlearning/intermediate-defining-your-message-structures-audit-emagiz-data-models--accessing-history-overview.png"></p>

When you click on this button you will see a grid showing you the detailed history of who has done what in the past on the CDM level.

<p align="center"><img src="../../img/microlearning/intermediate-defining-your-message-structures-audit-emagiz-data-models--showing-history-overview.png"></p>

Within this overview, you have the option to search on several indicators such as who made the change or what that person described they changed 

<p align="center"><img src="../../img/microlearning/intermediate-defining-your-message-structures-audit-emagiz-data-models--search-history-overview.png"></p>

### 3.1 Editing the CDM

Having a view of the history of the CDM adds value if you can register certain changes made on the CDM level. 
To correctly describe these changes made you rely on the person making the change. This is why it is of utmost importance that when you edit the CDM
you specify exactly what you have changed.

To edit the CDM you click on the Start Editing button located in the left bottom corner of your screen. 
The moment you have pressed Start Editing you can add, edit and delete entities and attributes on this canvas.

<p align="center"><img src="../../img/microlearning/intermediate-defining-your-message-structures-audit-emagiz-data-models--edit-mode-cdm.png"></p>

When you are satisfied with your changes you can press Stop editing. After you have pressed Stop editing you will see a popup.
In this pop-up, you have to define whether you have made a major change, minor change, or patch update to the CDM and describe what you have changed

<p align="center"><img src="../../img/microlearning/intermediate-defining-your-message-structures-audit-emagiz-data-models--new-version-popup.png"></p>

<p align="center"><img src="../../img/microlearning/intermediate-defining-your-message-structures-audit-emagiz-data-models--new-version-popup-filled-in.png"></p>

As you can see what you write down in terms of what you have changed is crucial so others can easily see what exactly has been changed.

##### Practice

## 4. Assignment

Edit the CDM within your (Academy) project and describe what you have changed after you are satisfied with your change. 
After this ask a colleague for a peer review to see if they can determine by looking at the History what has been changed.

## 5. Key takeaways

Having audit functionality on the eMagiz data model level provides traceability and accountability for a key aspect of your integrations.
To make sure that auditing can be done correctly the person that does the editing must make it clear what has been changed.

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz.

## 7. Silent demonstration video

<iframe width="1280" height="720" src="../../vid/microlearning/intermediate-defining-your-message-structures-audit-emagiz-data-models.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
</main>
</div>
</div>