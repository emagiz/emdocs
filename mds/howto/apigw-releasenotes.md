## Relesae notes API Gateway

This document describes the overall positioning and use of the API Gateway embedded into the Low-code, Enterprise iPaaS platform eMagiz. 


## Positioning & Key Concepts

The API Gateway is one of the key Integration patterns that eMagiz supports in the platform. Key concepts of the API Gateway in this context is that it allows to create an entry point for all published API's inside an IT landscape. Backend systems, micro-services or access to external systems can be published, so that either internal development teams and applications can access the specific APIs as part of business process execution.

A typical landscape could look like this. 


## Key considerations when to use the API Gateway integration pattern

Below is the list of considerations when to use the API Gateway.

One of the first angles to consider an API Gateway is when an integration in synchronous in nature. A business process is handled via a specific application, and that business process requires data from another (micro-)service and can only proceed once that reponse to that data request is returned successfully. This is a typical synchronous message interaction. The API Gateway is able to provide the exact operation to the application requesting the data.

The other important angle when to consider an API Gateway is to use the gateway concept as a mean to allow external & internal developments teams to connect to published APIs. On the one hand, Sales Orders from external clients might be send to the Gateway, or an internal microservice could be calling an API as part of a business process whereby the API reaches out to another (external) web services. Data is provided via the API Gateway.

Other considerations or key notes when to use an API Gateway are:
- Data is transactional in nature
- Data request is synchronous
- The backend provider of the operation must be online to return or process data - data is pushed
- Standardization of access to data is important 
- Dependency between developments should be reduced - less coupled services 
- Access to the same data can come in from many different systems


## Features

The API Gateway is fully embedded into the eMagiz Low-code Enterprise iPaaS so that users have a similar user experience when configuring the API Gateway, a Messaging integration or an Event Stream. 


