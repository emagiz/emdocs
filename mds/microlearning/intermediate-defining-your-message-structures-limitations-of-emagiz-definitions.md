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

# Limitations of eMagiz definitions

In this microlearning, we will focus on certain limitations when importing your definition in eMagiz. It is necessary to understand these limitations in order to make the correct choices before importing your definition into eMagiz.

Should you have any questions, please contact academy@emagiz.com.

- Last update: March 26th 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around learning which limitations you need to take into account when importing your definition
With eMagiz definitions we mean: Structured data models that represent how a message should look like at a certain point in the flow
With limitations we mean: Restrictions of what will and what won't work when importing your definitions

Identifying and knowing about these restrictions will improve your decision making the moment you want to import your definition

- Imported files cannot be larger than 1MB 
- xs:all statements cannot be represented in the data model.
- Iterations (maxOccurs) over a threshold of 50 are not accepted
- Cross reference between entities that could lead to an infinite loop are not accepted

##### Theory

## 3. Limitations of eMagiz definitions

In this microlearning, we will focus on certain limitations when importing your definition in eMagiz. It is necessary to understand these limitations in order to make the correct choices before importing your definition into eMagiz.

Identifying and knowing about these restrictions will improve your decision making the moment you want to import your definition

- Imported files cannot be larger than 1MB 
- xs:all statements cannot be represented in the data model
- Iterations (maxOccurs) over a threshold of 50 are not accepted
- Cross reference between entities that could lead to an infinite loop are not accepted

Below we will specify per limiations what this exactly means

### 3.1 Imported files cannot be larger than 1MB

As a normal user you are not allowed to upload files that are larger than 1MB. This to prevent people from uploading huge files that could potentially bring down the eMagiz portal for all users. In cases where you need to import a file that is larger than 1MB you need to contact your partner manager. This way we can analyze your exact needs and provide a tailormade solution that will help you import your definition.

### 3.2 xs:all statements cannot be represented in the data model

As specified before in earlier microlearnings, eMagiz defines the expected structure with the help of data models. Within a data model you need to specify the order in which entities and attributes follow each other. In XSD terminology this is called xs:sequence. In some cases your definition might have xs:all instead of xs:sequence. xs:all means that attributes and entities can arrive or be send in a random order. As this cannot be modeled out in a data model eMagiz will not support it.

In these cases you will have to change your definition to state xs:sequence everywhere the definition says xs:all. After that you can upload it without problems. Changing your definition in such a way could impact the validation of incoming messages. When the delivering party indeed sends its data in a random order everytime you need to take additional steps to ensure this will work in eMagiz. There are two alternatives when dealing with this problem:

- Write a custom XSLT that will transform the incoming message to a structured messages that you can validate via the tooling
- Use a custom XSD as validation and use the standard eMagiz tooling for your transformation, whereby you assume that your system definition has a defined structure

### 3.3 Iterations (maxOccurs) over a threshold of 50 are not accepted

To prevent weird results when it comes to the creation of data models we do not accept maxOccurs above 50. To succesfully import your definition you should change the maxOccurs setting to unbounded. This way eMagiz will succesfully import the definition. As of today we have never encountered a practical case where this caused issues.

### 3.4 Cross reference between entities that could lead to an infinite loop are not accepted

In some cases we see definitions in which entities keep referecing each other. This could cause an infinite loop to occur when trying to build up the correct structure of your system message. Therefore we do an initial check when importing your file to safeguard ourselves against creating infinite loops in our portal that will in the end break the eMagiz portal.

##### Practice

## 4. Assignment

Make sure that at least one of the attributes within one of your data models is set to Confidential
This assignment can be completed within the Design phase of your (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

Identifying and knowing about these restrictions will improve your decision making the moment you want to import your definition

- Imported files cannot be larger than 1MB 
- xs:all statements cannot be represented in the data model
- Iterations (maxOccurs) over a threshold of 50 are not accepted
- Cross reference between entities that could lead to an infinite loop are not accepted

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz.

## 7. Silent demonstration video

As this is a theoretical microlearning there is no video

</div>
</main>
</div>
</div>