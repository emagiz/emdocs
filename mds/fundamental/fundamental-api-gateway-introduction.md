<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/fundamental/index_academy_fundamental_all" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>
<div class="doc">
 
##### Intro

# eMagiz API Gateway
 
In this microlearning, we will introduce the most important concepts of the eMagiz API Gateway. The focus will be to address the key concepts of this pattern. Please refer to other Fundamentals to learn more about related items, and take a look at the relevant microlearnings available to learn how to configure an API Gateway in eMagiz.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: November 10th 2021
- Required reading time: 10 minutes

## 1. Prerequisites
- Completed the crashcourses of eMagiz


## 2. Key concepts
All concepts are discussed in the section below.

##### Theory
  
## 3. Introducing API Gateway

Tbe eMagiz API Gateway is the patterns in which a specific entry point is made available for external application (users) to connect to, and where a series of operations are listed that this application user can access to retrieve data from or send data to. Users & Roles are managed on a central level to mange the access to the various data sources.

<p align="center"><img src="../../img/fundamental/fundamental-api-gateway-introduction-1.png"></p>

### 3.1 Entry point for application users
The entry point is a REST/JSON based webservice that publically accessible via the eMagiz Cloud for external application users. There is no other type webservice possible, and all the operations inside this webservice are all REST/JSON based. In eMagiz this concept translates into an All Entry flow type.

### 3.2 Operations
An operation is defined as a an entry points in the API Gateway that allows a specific type of interaction with the data exposed. For instance, a user want to get the data for a specific order or would like to create an order via this entry point. In this example, there will be a GET Order and a POST Order operation. The regular WEbservice standards GET, POST, PUT, etc are possible - see below figure.

<p align="center"><img src="../../img/fundamental/fundamental-api-gateway-introduction-2.png"></p>
 
### 3.3 API Providers & Transformation
For every operation, there is a specific system that is connected to the operation and which actually gets the data or processes the data. That system or application or service is geared towards that specific piece of data and may have it's own connectivity requirements, security requirement or data structure. eMagiz will create a specific Exit Gate Flow type for this, so that all these requirements can be handled propertly. The figure below the Control Tower, Exact, AFAS and Address validator are the API providers

<p align="center"><img src="../../img/fundamental/fundamental-api-gateway-introduction-4.png"></p>

Each operation can have a Gateway Message and a System message for the specific API. In this way, standard eMagiz transformation tooling is made available to handle content and format transformations in the API Gateway.

<p align="center"><img src="../../img/fundamental/fundamental-api-gateway-introduction-5.png"></p>

### 3.4 Interaction type & error handling
The API Gateway follows a synchronous pattern which means there is always a request being made to the webservice, and that same webservice will always provide you with a response. The webservice will wait until the backend system that is delivering the response is ready to send that response. 

In all cases, a specific response is provided by the web service using HTTP response codes (standard definition used). In case a specific HTTP response code is returned that includes a specific error, then the requestor / application user is responsible for handling the error that is returned. That is by design as the synchronous nature of these request imply that calling application needs to make a decision to continue to the next functional step or alike. In any case it is different and specific for each application user.

eMagiz does allow to influence some of these response codes by specific information per HTTP responses codes. Or provide custom responses.

### 3.5 Centralized User Management
In the context of an API Gateway, user management means the mechanism whereby users are granted access to a specific set of operations. User Management in eMagiz has the ability to define users and roles. The user will have the access credentials to access the API Gateway in the first place. Options are OAuth2.0 or API Key. Users are assigned a role which defines to what operations access has been given. In this way the access to the gateway is handled in a central manner and the data exposed is protected properly. Credentials are to be submitted to application users on a separate note.

### 3.6 API Disovery
External appliction users can discover the operations via an online Portal - the SwaggerUI technology is used for that purpose. In that online section, the user can see all the published operations. For operation all the required information is displayed to propertly understand how to connect to the API. That includes the request and response definitions, parameters, naming, response codes and so on. Once the credentials have been provided the application user can try out the operation. 

<p align="center"><img src="../../img/fundamental/fundamental-api-gateway-introduction-3.png"></p>


### 3.6 Architectural components

A simplied picture below is list to illustrate the overall architecture of API Gateway in the eMagiz Cloud.  

<p align="center"><img src="../../img/fundamental/fundamental-api-gateway-introduction-6.png"></p>

##### Practice

## 4. Key takeaways

- API Gateway can serve as a single entry point for all external or intern application users
- API Gateway can simplify the IT landscape by offering a reusable entry point 
- API Gateway is a synchronous pattern by default
- API Gateway leverages the standard capability of eMagiz around deployment, transformation and business owner interaction

##### Solution

## 5. Suggested Additional Readings

- https://www.emagiz.com/en/api-gateway-en/
- Crashcourse API Gateway			: https://emagiz.github.io/docs/microlearning/crashcourse-api-gateway-index
- API Management					: https://emagiz.github.io/docs/microlearning/intermediate-api-management-index
- Transformations in API Gateway	: https://emagiz.github.io/docs/microlearning/intermediate-configuring-the-api-gateway-index
- Testing the API Gateway			: https://emagiz.github.io/docs/microlearning/intermediate-testing-emagiz-api-gateway-index
- Advanced config API Gateway		: https://emagiz.github.io/docs/microlearning/advanced-api-management-index


## 6. Silent demonstration video


</div>
</main>
</div>
</div>