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

## Architectural setup eMagiz

eMagiz consists of various systems communicating with each other to make the process of developing the process layer and subsequently running the message layer as secure and stable as possible for our customers.

The picture shown below shows how these various entities interact with each other on both process aswell as messaging layer.

<p align="center"><img src="../../img/howto/localconnector-infrastructure-view.png"></p>

## Strengthen your data's security with encryption during transport

### Data 'in transit'

As an integration provider we transport data between applications. To ensure that the transport of this data is as secure as possible several measurements have been set up to keep the data confidential.

Let us first look at the data 'in transit'. This is the phase of the process where data is interchanged between flows within the eMagiz platform (i.e from entry to onramp or offramp to exit) via the orchestration of the JMS server on the messaging layer. This is nicely shown in the picture below.

<p align="center"><img src="../../img/howto/security-guide-0.png"></p>

Data ‘in transit’ is temporarily stored on an encrypted filesystem with the help of encryption algorithms. 
For the cloud eMagiz uses the AES-256 encryption algorithm. 
For on-premise runtime installations eMagiz uses the AES-128 encryption algorithm. 
These algorithms make sure that even if outside sources should be able to get to the data on that encrypted filesystem they won’t be able to read the data.
That way the data is kept confidential.

### Transport Layer Security

To ensure the integrity of data in the transport layer of eMagiz, eMagiz uses the TLS protocol. This means that all client-server communication is secured via TLS. In eMagiz this is implemented as follows: The necessary certificates of the client(s) are trusted by the server and the server is trusted by the client(s). The relevant information is stored in keystores and truststores that are unique per project. This ensures that data cannot be send to other client projects or to other environments within your project.
In other words it prevents others from eavesdropping on your channels. eMagiz follows the standard guidelines when setting up TLS by making sure that the configured trusted certificate authority (CA) bundle that your messaging server uses to verify client connections, is limited to only the CA used for your nodes, preferably an internally managed CA.

### Data exchange between application and integration

Because eMagiz provides the integration between two or more applications via the eMagiz platform the point at which the data is interchanged between application and integration is a critical part of the integration in terms of security.
eMagiz offers users the tools to set up integrations and end-points in a secure manner. eMagiz supports well-known market standards, including:

	-	OpenID Connect
	-	WS-Security
	-	API Keys in combination with HTTPS/SSL
	-	SOAP Authentication
	-	OAuth2.0
	-	Basic Authentication
	
This way each connection between the application and the integration (end-point) can be secured in a proper manner and gives the flexibility to confer with the external application which method suits their needs the best. 

### Availability of data

The availability of data in eMagiz is quaranteed due to the queue (messaging) and topic (event streaming) functionality that are used to transport data. In case a consuming entity (which can be another queue, topic, external application or else) is not able to consume the data the data will be temporarily stored in a secure manner in the encrypted filesystem we discussed above.
In case of event streaming the data is temporarily kept on the topic within the kafka cluster. For more detailed information on the security surrounding our kafka event streaming solutions please see ........

## Access to runtime / machine

In the last section we looked at data 'in transit'. In this section we take a step back and look at access to the runtime / machine that holds the process flows that process your data. As you can imagine anyone with access to a machine where runtimes are running on can influence the availability, integrity and confidentiality of data.

<p align="center"><img src="../../img/howto/definition-emagiz-model.png"></p>

eMagiz offers two 'places' were you can install runtimes. Per 'place' we will look a bit deeper at which security measures are taken and should be taken in accordance with you to ensure the availability, integrity and confidentiality of the data

### On-premise

On-premise means that the runtimes are running on a machine outside the direct control of eMagiz. This means that the machine is running under the control of the customer that implements eMagiz within their IT landscape.

Because the machine is outside the direct scope of control of eMagiz it becomes a joint effort between eMagiz and you as a customer to make sure that not everyone can access this machine. This becomes even more important when working with file based actions as part of your integration. 
Advice would be to govern this via an IDP (i.e. Azure AD) so you can set up roles that have access to the machine or parts of the machine (i.e. some files).

### Cloud

In the eMagiz cloud the access is restricted to those who have a legitimate reason to access it based on SLA level agreements. This means support engineers, consignment employees and your bus owner have access to your specific cloud setup.
This access is per role furthermore limited. This means that consignment employees and bus owners can only see the logging of the runtimes on the machine and the ability to start/stop machines.

Support engineers have the ability to see more in order to analyze problems on a lower level.

All other users don't have access to the cloud setup as there is no need for access because they can perform the relevant actions on the cloud via the eMagiz portal. For more information on how please see [eMagiz Cloud Management](managing-emagizcloud.md)

## Security guidelines for cloud setups

In this section we take a closer look at the cloud setup in general. Here we will focus on high level security measurements because specifying security measumerents at the data leve are already discussed in the previous section.

### Cloud setup

In the picture shown below you see a standard dual-lane setup of an eMagiz instance within the eMagiz Cloud. A single-lane setup looks similar but only consists of one core machine.
This gives a good insight in how messages are flowing through the cloud, which measure are taken for monitoring and auto healing and where data is temporarily stored 'in transit'. 

<p align="center"><img src="../../img/howto/security-guide-1.png"></p>

We would like to use this picture to explain certain components within the cloud from a security perspective. We will start at the outside and work our way inwards.

### Cloud location

Within the AWS cloud there are a number of regions were your cloud setup can be running. Examples of these regions are us-east-1, af-south-1, ap-northeast-1, eu-central-1.

As you can see in the picture eMagiz cloud slots are running within the eu-central-1 region. This region is located in Frankfurt and falls therefore under european data and security laws such as the GDPR.

### Cloud slot (VPC)

Within this region a unique cloud slot per customer is assigned. In the picture this is represented as a Virtual Private Cloud (VPC). Setting up a VPC lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways.

Incoming data from the internet passes through a load balancer to route data randomly to one of the core machines containing the runtimes holding the process flows. The setup of a VPC is governed by what we call a cloud template.


### Cloud template
 
This cloud template, designed by eMagiz defines the setup of your cloud instance.
The following parts of the cloud setup are configured here:

- Java version
- OS version (Linux)
- Runtime version
- Auto healing
- Monitoring
- Notification options

Staying on the latest cloud template version guards yourself against vulnerabilities in older versions of Java and OS for example. In addition it gives the user more options for monitoring the health of the cloud environment reducing the risk of a loss of availability of data (in a timely manner) without comprimising the integrity of the data.

### Cloud access

In the eMagiz cloud the access is restricted to those who have a legitimate reason to access it based on SLA level agreements. This means support engineers, consignment employees and your bus owner have access to your specific cloud setup.
This access is per role furthermore limited. This means that consignment employees and bus owners can only see the logging of the runtimes on the machine and the ability to start/stop machines.

Support engineers have the ability to see more in order to analyze problems on a lower level.

All other users don't have access to the cloud setup as there is no need for access because they can perform the relevant actions on the cloud via the eMagiz portal. For more information on how please see [eMagiz Cloud Management](managing-emagizcloud.md)


## eMagiz iPaaS Portal Security considerations
The eMagiz Portal provides access to users to manage their eMagiz integration configurations. It provides access to all the features to develop, deploy and manage integrations across Test, Acceptance and Production environments.

### User access to https://my.emagiz.com
User can be added with their email adress by the eMagiz Partner Manager, upon which the user gets an email to sign-in. A temporary password is created and emailed as well, which has to be changed at the first login to the iPaaS Portal. Users are connected to organizations in eMagiz.

### Users access to Integration Projects
Users can be added to Integration projects, which hold all the configurations required to run the different integrations for the TAP environments. Integration projects are connected to organizations in eMagiz to ensure the integration project remains within limits of the license agreeements. Users can be added to integration projects of the organization where the user belongs to. Users can't be added to integration projects of other clients. 

### User authorizations to Integration projects.
Every integration project has a bus owner who can distribute rights across functionalities and environments. In the picture below, one can see the various options available across the Integration Life Cycle (ILM) Phases Capture through Manage. The bus owner manages the user permissions and needs to have the MFA authentication level passed before making any changes. 
In case an Edit permission is granted on a ILM phase, all the sub-options can be used. Bus owners are assigned to integration projects by eMagiz Administrators

<p align="center"><img src="../../img/howto/security-guide-accessrights.png"></p>

### Partner user access to Client environments
Partner organizations exit in eMagiz. Bus owners can select user from their own organization or from the connected partner organization. The connection between client and partners organization is managed by eMagiz administrators

### Summary of relevant access to environments for eMagiz Administrators
eMagiz Administrators can view all integration projects, and has the bus owner rights for all integration projects. 


## eMagiz GDPR compliancy

### Personal Data we process
We process the following Personal Data as a controller

| Personal Data | Purpose | Legal basis | Additional Information | Retention Period |
| Invitations to the eMagiz Platform |  Allow you to join the platform. | Legitimate interest | If you choose to invite another person to the eMagiz Platform, we will ask you for the name and email address of that person. We will automatically send that person an invitation email to visit the eMagiz site, to create an account or join your bus. | | 
| Data you leave on our sites at our blog, Q&A or Store | Interaction with our users. Providing our users with information about the service. | Legitimate interest | 
Note that information you leave on the blog or Q&A is public and can also be seen and used by others. We are not responsible for the Personal Data you choose to submit in these blogs and forums.| As long as it provides useful information for our users.| 
| IP address, your activity on our site and device and browser information | Insight in behavior of website visitors. | Legitimate interest | We use Google Analytics to provide website visitors with an optimal user experience. See the section on Google Analytics for more information. | | 
| IP address, your activity on our site and device and browser information
| Correct display, optimization and maintenance of our websites. | Legitimate interest | Maintained by our website hosting provider. | 6 months |
| Contact details | Direct marketing |Legitimate interest | We process this information to contact you about our products and services. You can opt out at any time | Until we have no more use for the data, or you opt out.| 

We do not make use of automated decision-making based on personal data.

###Protection of Personal Data
We make reasonable efforts to ensure a level of security appropriate to the risk associated with the processing of Personal Data. We maintain organizational, technical and administrative measures designed to protect Personal Data within our organization against unauthorized access, destruction, loss, alteration or misuse. Our Information Security Management System is ISO 27001 certified. Your Personal Data is only accessible to a limited number of personnel who need access to the information to perform their duties. Unfortunately, no data transmission or storage system can be guaranteed to be 100% secure.
We store your Personal Data within the European Union. We ensure that our service providers do the same. In case your Personal Data is processed or stored in the United States of America, we ensure that our service provider is certified under the EU-U.S. Privacy Shield Framework.

###Personal Data we share
We may share your personal data with our service providers (for example our hosting providers). We make reasonable efforts to ensure that they have a level of security appropriate to the risk associated with the processing of personal data. We have a Data Processor Agreement with our service providers to ensure that their processing of your data is according to our instructions and within the bounds of the GDPR.


### Personal data in messages processed by the platform



