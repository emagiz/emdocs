This document discusses how you can manually host a REST webservice outside the API management layer of eMagiz.
The main idea of hosting a webservice, whether it be SOAP/XML or REST/JSON (or any other combination) is that the process you are supporting wants to be informed in real time or wants to execute actions in real time without any support from the integration. In other words you want the application to push the requests to eMagiz and from there to another application instead of having to pull the data out of an application. 
In this how to we will focus on the REST webservice and how you can host this in eMagiz through some simple steps.
To summarize, hosting a REST webservice gives you:
-	A way to listen for messages instead of actively needing to pull them.
-	A way to receive messages via various HTTP methods (GET, PUT, POST, DELETE, etc.)



## Best practices

-	Don’t change your process when executing Capture and Design. Those steps don’t change if you want the output of what is being delivered on your REST endpoint transformed to a CDM and beyond
-	Use naming conventions to make it clear to the calling party what the build up of the endpoint is, which methods are allowed and which contentTypes are allowed
-	Keep the connectivity in the entry and the transformation in the onramp
-	Use one HTTP Inbound Gateway per HTTP Method


## How-to steps Hosting a REST webservice

Follow these steps carefully in order to acquire the desired result. If a step is unclear or you are not able to follow it, please contact your eMagiz partner manager.
1.	If the system for which you want to host the REST webservice is new start with step 2. If you already have a system Captured continue with step 6
2.	Navigate to Capture and add a system to the canvas
3.	Fill in the System name and information on the system
4.	Draw a line representing a message type from the system to eMagiz in the middle
5.	Fill in the relevant details based on system and message type specifics
After this step you have successfully finished Capture (for hosting a REST webservice)
6.	Navigate to Design and double click on the system for which you want to host a REST webservice
7.	Select the option Combined entry connector
8.	Select Custom under Entry connector type
9.	If applicable, execute the same steps in Design as you normally. i.e create / change CDM, add system message, message mapping, update architecture, etc.
After this step you have successfully finished Design (for hosting a REST webservice)
10.	Navigate to Create -> Add integrations
11.	Select the flow you have just registered via Capture and Design
12.	Press Save Selection
13.	Navigate back to Create. eMagiz will have added the flow including the all entry
14.	Open the all entry
15.	Add the support object called Jetty Server
16.	Open the support object after naming it
17.	Select a connector. When running in AWS or if you want to handle the authentication without a client certificate requirement the Select channel connector is the option of your choice. In most cases this is used
18.	Fill in the port
19.	Select for handler type the Servlet Context Handler. This way you can set up the endpoint through each HTTP inbound gateway that you need in the all entry
20.	Type in the context path. A option could be to go for /rest or /api or simply /. This will become part of the endpoint later on
21.	Select as Servlet the HTTP Inbound endpoint dispatcher. This does the following for you: A servlet that dispatches requests to HTTP inbound gateways and HTTP inbound channel adapters based on their request mapping settings. For more information see the help text provided with the component itself.
22.	Give the servlet a name so you can tell what the function is.
23.	Add a servlet mapping and fill in the required values. The servlet name needs to match the name you have just created in step 20. The path should be something that makes it clear to the caller what he is calling. A categorization could be done here (i.e /schades/* or /orders/* or /invoices/*)
24.	Press Save
After this step you have successfully created the Jetty server that will host the collection of endpoints of your REST webservice
25.	Add a HTTP Inbound Gateway to the flow and create two channels to which it can connect
26.	Define the path that is specific for this endpoint (i.e /address or /invoicelines or v1/reports)
27.	Define the supported methods for this specific Gateway (i.e. GET, POST, DELETE)
28.	Define under the Advanced tab the Request payload type as java.lang.String for readability
After this step you have successfully created an HTTP Inbound Gateway that listens to specific methods on a specific endpoint which you can test and works
29.	Apart from the mandatory options (defined in step 26 till 28) there are many optional options, such as defining params, which contentType(s) are consumed and produced. For more information on these please see the help text in the component itself
30.	You can verify if your endpoint works by deploying it on a local runtime and call the endpoint (via Postman) you have created in the previous steps. The structure is as follows: https://host:port/contextPath/servletPath/pathInfo?queryString
31.	If everything works correct (be aware, if you run it locally you need http in your endpoint) you should receive a 200 OK and a payload. Easiest way to test the validity of your setup is to create a POST call that gives back what you have posted.
After this step you have verified that the endpoint itself can be called. Next steps could be to add authentication or other checks in order to give back 401, 404, 403 etc.










