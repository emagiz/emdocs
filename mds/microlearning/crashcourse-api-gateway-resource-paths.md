# HTTP Resource (Paths)

In this microlearning we will focus on learning about HTTP Resource (Paths).
A crucial part of setting up your (API) Gateway with the help of RESTful services is 
knowing to which resources (i.e. Order, Client, Employee) you want to give external parties access via your (API) Gateway.

Should you have any questions, please contact academy@emagiz.com.

- Last update: February 11th 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around HTTP Resource (Paths) in conjuction with the API Gateway solution of eMagiz.
With HTTP Resource Paths we mean: Identify the resource (i.e. Client, Order, Employee) and define the descriptive path (i.e. /v1/order, /v1/order/{uuid}) a external party can call to execute the operation
With API Gateway we mean: A collection of RESTful API operations that can be published to the outside world in order to give them access to applications that are linked to your business process

When determining the correct resource path to expose to the outside world start at what you want to make publicly available.
For example, when you want to make it possible for external parties to retrieve a collection of orders without any filter a valid resource path can be:
- /orders

If you have multiple resources that you want to make available that all have something to do with the order process you could add each of them to a 'group' to add a extra layer of information:
- /order-management/orders
- /order-management/trips

To determine the correct notation also take into account how the backend system that you want to expose via the API Gateway has determined their HTTP Resource (Paths). 
If this adheres to the best practice simply use that. More on that specific relation in later microlearnings.

A list of best practices can be found here:
https://restfulapi.net/resource-naming/

## 3. HTTP Resource (Paths)
When determining the correct resource path to expose to the outside world start at what you want to make publicly available.
For example, when you want to make it possible for external parties to retrieve a collection of orders without any filter a valid resource path can be:
- /orders

If you have multiple resources that you want to make available that all have something to do with the order process you could add each of them to a 'group' to add a extra layer of information:
- /order-management/orders
- /order-management/trips

To determine the correct notation also take into account how the backend system that you want to expose via the API Gateway has determined their HTTP Resource (Paths). 
If this adheres to the best practice simply use that. More on that specific relation in later microlearnings.

A list of best practices can be found here:
https://restfulapi.net/resource-naming/

In the following microlearning on HTTP Operations we will bring the HTTP Resource (Paths) together with the HTTP Operations. 
That combination is the basis for any integration that runs via the API Gateway.

## 4. Assignment

Read up on the best practices when it comes to the naming of HTTP Resource Paths and see if you can relate this to the eMagiz implementation.
This assignment can be completed with the help of a associated Mendix project linked to the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Start at the backend operation
- Determine usability of what is provided to you
- Take action based on that analysis

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz and read the following links:
- https://restfulapi.net/resource-naming/

## 7. Silent demonstration video

As this is a more theoretical microlearning no demonstration video is created. See you in the next microlearning.