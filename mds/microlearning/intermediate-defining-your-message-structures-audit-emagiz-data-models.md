<div class="ez-academy">
	<div class="ez-academy__body">
		<main class="micro-learning">
		<ul class="doc-nav">
			<li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-defining-your-message-structures-index" class="doc-nav__link">Home</a></li>
			<li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
			<li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
			<li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
			<li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
		</ul>

<div class="doc">

##### Intro

# Audit eMagiz Data Models

In this microlearning, we will focus on how you can audit the three eMagiz data models (CDM, API Gateway Data Model, Event Streaming Data Model) 
within your project to see which changed have taken place and what you should do when changing something in these data models to make it auditable.

Should you have any questions, please contact academy@emagiz.com.

- Last update: January 22th 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Understanding of the data model concept

## 2. Key concepts
This microlearning centers around auditing your eMagiz project on the eMagiz data model level.

By audit we mean: Making it clear who changed the data model at a certain moment in time.

With data model we mean: The data model that defines the data structure and relationships between these data structures that are generic, uniform, and representative of how this data is looked upon within our organization.

Auditing the eMagiz data models can be done by navigating to the specific data model in question in the Design phase and selecting the button called History located in the bottom bar.

##### Theory
  
## 3. Audit eMagiz Data Models

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