# eMagiz security guide

eMagiz is built with security in mind to protect your data. Protecting your data is a joint responsibility between you and eMagiz. The eMagiz security features enable you to empower your users to do their jobs safely and efficiently and gives you the opportunity to transport data safely between applications.

## eMagiz security basics
The eMagiz security features help you empower your users to do their jobs safely and efficiently. eMagiz limits exposure of data to the users that act on it. Implement security controls that you think are appropriate for the sensitivity of your data. We'll work together to protect your data from unauthorized access from outside your company and from inappropriate usage by your users.

## Authenticate users
Authentication means preventing unauthorized access to your organization or its data by making sure each logged in user is who they say they are.

## Give users access to data
Choosing the data set that each user or group of users can see and more importantly manipulate is one of the key decisions that affects data security. You need to find a balance between limiting access to data, thereby limiting risk of stolen or misused data, versus the convenience of data access for your users.

## Monitoring your project’s security

Track login history, monitor setup changes, and take actions based on this.

## Monitoring the environment via Manage

Monitoring your (Production) environment helps you monitor and detect deviations within your environment in near real-time. All errors and relevant logging is stored for a limited period within eMagiz for auditing or reporting purposes. Furthermore notifications can be send to people to alert them of a potential loss of data integrity.

## Strengthen your data's security with encryption during transport

As an integration provider we transport data between applications. To ensure that the transport of this data is as secure as possible several measurements have been set up to keep the data confidential.

Let us first look at the data 'in transit'. This is the phase of the process where data is interchanged between flows within the eMagiz platform (i.e from entry to onramp or offramp to exit) via the orchestration of the JMS server on the messaging layer. This is nicely shown in the picture below.

<p align="center"><img src="../../img/howto/security-guide-0.png"></p>

Data ‘in transit’ is temporarily stored on an encrypted filesystem with the help of encryption algorithms. 
For the cloud eMagiz uses the AES-256 encryption algorithm. 
For on-premise runtime installations eMagiz uses the AES-128 encryption algorithm. 
These algorithms make sure that even if outside sources should be able to get to the data on that encrypted filesystem they won’t be able to read the data.
That way the data is kept confidential.

To ensure the integrity of data runtimes can only communicate with the JMS server via client vs server setup. This basically means that the necessary certificates of the client(s) are trusted by the server and the server is trusted by the client(s). This way you create a two-way ssl connection. The relevant information is stored in keystores and truststores that are unique per project. This ensures that data cannot be send to other client projects or to other environments within your project.


Because eMagiz provides the integration between two or more applications via the eMagiz platform the point at which the data is interchanged between application and integration is a critical part of the integration in terms of security.
eMagiz offers users the tools to set up integrations and end-points in a secure manner. eMagiz supports well-known market standards, including:

	-	OpenID Connect
	-	WS-Security
	-	API Keys in combination with HTTPS/SSL
	-	SOAP Authentication
	-	OAuth2.0
	-	Basic Authentication
	
This way each connection between the application and the integration (end-point) can be secured in a proper manner and gives the flexibility to confer with the external application which method suits their needs the best. 

The availability of data in eMagiz is quaranteed due to the queue (messaging) and topic (event streaming) functionality that are used to transport data. In case a consuming entity (which can be another queue, topic, external application or else) is not able to consume the data the data will be temporarily stored in a secure manner in the encrypted filesystem we discussed above.

In case of event streaming the data is temporarily kept on the topic within the kafka cluster. For more detailed information on the security surrounding our kafka event streaming solutions please see ........

## Security guidelines for cloud deployments

Understand and guard against vulnerabilities whilst using the Cloud setup by eMagiz.