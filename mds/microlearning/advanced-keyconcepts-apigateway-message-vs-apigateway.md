<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-keyconcepts-apigateway-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Considerations for API Gateway or Messaging

In this microlearning we'll take a moment to discuss several considerations for making the right choice between the two patterns

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: December 2021
- Required reading time: 10 minutes


## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- Completed the relevant microlearnings Key Concepts API Gateway (level crash course to intermediate)
- Completed the relevant microlearnings Key Concepts Messaging (level crash course to intermediate)

## 2. Key concepts
Please refer to the following Fundamentals to learn the key concepts of both patterns

- [eMagiz API Gateway](../../docs/fundamental/fundamental-api-gateway-introduction)
- [eMagiz Messaging](../../docs/fundamental/fundamental-event-streaming-introduction)

##### Theory
  
## 3. Considerations for selecting Messaging or Event Streaming

The following sections are helpful to understand what things to consider in selecting the right pattern. 

- **Synchronous**
	- Both patterns in this discussion are synchronous in nature. In case a asynchronous message is the right choice, pelase refer to the relevant microlearning that compares Messaging and Event Streaming
	
- **Data**
	- Both patterns can handle similar type data - usually record based
	
- **Online vs. offline**
	- For Messaging, the delivering and receiving system need to be online with high availability ratio's in order to process the messages. The same is true for a backend API provider which needs to be online to provide or consume data from API operations

- **Error handling**
	- In the case of an API Gateway, the requesting application needs to be handle the error messages that are returned by the API gateway in case there are any. The API Gateway provides the errors from the backend API directly back to the requestor who can then decide how to process the request.
	- For Messagaging, the errors that are generated are pushed inside the general error process of eMagiz and displayed in the Error Dashboard in the Manage phase. However, the requestor also gets the error messages back from the Messaging system in order to handle these properly
	
- **Contract & communication**
	- Messaging required a fixed contract between the message definitions that are exchanged. A change of definition would result in validation issues and therefore more communication is required
	- For an API Gateway solution, the contract is published via the API Gateway outwards. The basic idea is that the data definition is fixed and standardized, and that requesting application will adapt their request to this definition. In that sense the API Gateway offers standardization in the landscape
	
- **Technical disqualifiers**
	- For an API Gateway, the requestor needs to be able to call a REST based webservice using JSON formatted messages.
	- Messaging allows other web services such as SOAP, but can also handle XML for instance

- **Centralized User Management**
	- API gateway offers a easy to configure user management capability to protect operations. Users and roles can be designed in the Design phase, and various authentication methods are allowed such as OAuth2.0 and API Keys. eMagiz offers easy to use configurations for that
	- For Messaging, no such user management options exit and all needs to be created inside the flows that handle the requests & replies.

##### Practice

## 4. Assignment

There is no assignment for now in this microlearning

## 5. Key takeaways

- There are a set of considerations to make decisions for API gateway vs. messaging
- Make sure to read the eMagiz Fundamentals properly before taking this section into account in your project

##### Solution

## 6. Suggested Additional Readings

Take a moment to read the following link https://emagiz.github.io/docs/usecase/index_academy_usecase_pattern_discovery

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video that accompanies this microlearning.

</div>
</main>
</div>
</div>