# Setting up exit gate

In this microlearning we will focus on setting up the exit gate for the API Gateway.
This exit gate ensures that the message is delivered to the backend operation and that the response of the backend operation is given back to the client calling the API.

Should you have any questions, please contact academy@emagiz.com.

- Last update: February 11th 2021
- Required reading time: 3 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around setting up the exit gate for the API Gateway solution of eMagiz.
With exit gate we mean: The piece of functionality that connects to the backend operation to execute the action on behalve of the client that is calling the API
With API Gateway we mean: A collection of RESTful API operations that can be published to the outside world in order to give them access to applications that are linked to your business process

Exit gate is created by eMagiz based on the configuration in Design. In passthrough cases you only need to add authentication.
In cases of transformation you need to specify the outbound component (i.e. HTTP, Web service, JDBC, SFTP etc.) and the authentication.

## 3. Setting up exit gate

Each backend operation has a specific exit gate that will handle all incoming traffic, connect to the backend operation and send the response back to the client that is calling the API.
The exit gate can process up to five calls at the same time. The moment the response is delivered to client 1, the exit gate will continue with the message of client 6.

With this setting we already scale the API Gateway in such a way that it can handle concurrency and peaks in traffic. For most use cases these settings will suffice.

eMagiz will generate almost everything for you when you transfer a API integration to Create. 
There are however some things you need to change depending on the choices made in Design and based on the required authentication method.

In case you have a passthrough case and the authentication method can be handled via a REST template (i.e. basic, oauth, azure) you only need to configure this specific authentication mechanism.

In case you have a passthrough case and the authentication cannot be handled via a REST template you need to set up the authentication yourself.

In case you have a transformation case you need to configure the outbound component + the accompanying authentication.

In the most standard case eMagiz will auto generate the following flow for you

<p align="center"><img src="../../img/microlearning/ml-configure-exit-gate--auto-generated-flow.png"></p>

Just as with the entry gate we try to auto generate as much as possible to make your life easier the moment you start in the Create phase.

## 4. Assignment

Open the exit flow, add basic authentication as authentication method and press Stop Editing.
This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Each backend operation has a specific exit gate that will
	- Handle all incoming traffic destined for that backend operation
	- Connect to the backend operation
	- Send response back to the client that is calling the API
- eMagiz will automatically build the biggest portion of the exit gate for you
- Some manual changes are necessary

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz.

## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned. Disclaimer, you only see the eMagiz part but if you follow the above steps you are good to go!

<iframe width="1280" height="720" src="../../vid/microlearning/microlearning-setting-up-exit-gate.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>