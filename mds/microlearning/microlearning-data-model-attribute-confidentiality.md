# Data Model - Attribute Confidentiality

In this microlearning we will focus on identifying which attributes within your data model(s) are deemed confidential and how you can register this in eMagiz.

Should you have any questions, please contact academy@emagiz.com.

- Last update: January 22th 2021
- Required reading time: 3 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This micro learning centers around making attributes confidential
With attributes we mean: A data element within a message (i.e. Name, BSN, EmployeeID)
With confidential we mean: Information that must be only accessible to those that need access to that (part of the) data

Identifying and registering whether an attribute is confidential can be done on all data models known in eMagiz:

- CDM
- API Gateway Data Model
- Event Streaming Data Model
- System messages

## 3. Data Model - Attribute Confidentiality

Within the eMagiz platform you can register whether certain attributes are confidential on all data models that are available in the platform:

- CDM
- API Gateway Data Model
- Event Streaming Data Model
- System messages

Below we give some more details based on a example on CDM level. This example can be applied in the same manner on any other data model in eMagiz

### 3.1 Registering an attribute as confidential

On data model level (i.e CDM) in eMagiz you can register whether attributes are confidential or not. 
The default is that no attribute in any of your data models is confidential. 
By navigating to Design and opening your data model you have the option to Edit attributes (while in Start Editing mode) via a right click to access the context menu

<p align="center"><img src="../../img/microlearning/ml-data-model-attribute-confidentiality--edit-attribute-context-menu.png"></p>

Let's say that I want to give my Users a grade based on the learning path they have completed. 
As you can imagine a grade might not be something that everyone has to know so you could make this attribute confidential.

<p align="center"><img src="../../img/microlearning/ml-data-model-attribute-confidentiality--edit-attribute-set-confidential.png"></p>

The result of pressing Save is that a lock icon will appear on data model level indicating that the attribute in question is deemed confidential within the context of your project.

<p align="center"><img src="../../img/microlearning/ml-data-model-attribute-confidentiality--confidential-overview.png"></p>

This icon not only shows on data model level but is also visible while performing a message mapping. 
This way you can quickly identify while doing a message mapping whether certain attributes are confidential so you can take precautions on it.

<p align="center"><img src="../../img/microlearning/ml-data-model-attribute-confidentiality--confidential-message-mapping.png"></p>

## 4. Assignment

Make sure that atleast one of the attributes within one of your data models is set to Confidential
This assignment can be completed within the Design phase of your (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Identifying and registering whether an attribute is confidential can be done on all data models known in eMagiz:
	- CDM
	- API Gateway Data Model
	- Event Streaming Data Model
	- System messages
- Registering an attribute as confidential can be done by switching a boolean
- Confidentially of attributes is seen across Design when looking at data models and message mappings.

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the helptext provided by eMagiz.

## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned.

<iframe width="1280" height="720" src="../../vid/microlearning/microlearning-data-model-attribute-confidentiality.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>