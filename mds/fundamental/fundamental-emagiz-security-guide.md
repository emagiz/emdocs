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

# eMagiz Security Guide
 
In this fundamental, we will zoom in on how the various parts of the eMagiz landscape can be viewed from a Security perspective. We will look at the Cloud, on-premises, data within eMagiz, external communication, and the portal during our journey. After this journey, you should have a solid understanding of what role security plays in each of the parts of the eMagiz architecture. Note that protecting your data is a joint responsibility between eMagiz and you. This fundamental aims to clarify the security measures eMagiz has taken in the eMagiz platform. This way, you can assess the eventual additional steps you need to take to ensure that the eMagiz service cooperates securely with the rest of your application and integration landscape.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: February 17th, 2022
- Required reading time: 15 minutes

## 1. Prerequisites
- Some context on cloud functionality will be helpful.

## 2. Key concepts
- Protecting your data is a joint responsibility between eMagiz and you
- The repository is read-only for clients
- Data in the Cloud is kept within your VPC
- Production data in the portal is behind an MFA check

##### Theory
  
## 3. eMagiz Security Guide

In this fundamental, we will zoom in on how the various parts of the eMagiz landscape can be viewed from a Security perspective. We will look at the Cloud, on-premises, data within eMagiz, external communication, and the portal during our journey. After this journey, you should have a solid understanding of what role security plays in each of the parts of the eMagiz architecture. Note that protecting your data is a joint responsibility between eMagiz and you. This fundamental aims to clarify the security measures eMagiz has taken in the eMagiz platform. This way, you can assess the eventual additional steps you need to take to ensure that the eMagiz service cooperates securely with the rest of your application and integration landscape.

### 3.1 Architectural setup eMagiz

eMagiz consists of various components communicating to develop the process layer and subsequently run the message layer as secure and stable as possible for our customers.

1. In the eMagiz integration project, various flows are created that work together to realize the integration. The different types are shown on the top of the picture below: Entry, Exits, Offramps, onramps, and routing flows.
2. These flows are then deployed together with a specific build number (contains framework components to make these flows work) into a runtime (java based application container). 
3. These runtimes run on Cloud machines that contain Cloud templates (all required components to make the Cloud machine operational such as OS, Java runtime version, and more).

The top part of the picture depicts the eMagiz repository. All relevant (open-source) libraries needed to run flows on a connector are stored within this repository.

To prevent unauthorized access to this repository, the following measures have been taken
-   Client runtimes can access the repository via a username/password combination through a one-way SSL connection (encrypted) and read the contents of the repository
-   eMagiz developers that need to upload bundles can access the repository through a one-way SSL connection (encrypted)
-   A bitbucket pipeline will be created soon to enable automatic updates. This data pipeline will also need a unique username/password combination along with the fact that the connection itself is a one-way SSL connection (encrypted)
-   The repository is read-only for clients. This means that even if someone gets their hands on a username/password combination, they do not have sufficient rights to alter anything in the repository. They can only read the data that is kept in the repository.


<p align="center"><img src="../../img/fundamental/fundamental-emagiz-security-guide--definition-emagiz-model.png"></p>


### 3.2 Security Guidelines - Cloud

In this section, we take a closer look at the cloud setup in general. Here we will focus on high-level security measurements because we already specified security measurements at the data level.

#### 3.2.1 Cloud setup

The picture below shows a standard double-lane setup of an eMagiz instance within the eMagiz Cloud. A single-lane design looks similar but only consists of one core machine.
This gives insight into how messages flow through the Cloud, which measures are taken for monitoring and auto-healing, and where data is temporarily stored 'in transit.' 

<p align="center"><img src="../../img/fundamental/fundamental-emagiz-cloud-inner-workings--customer-level-overview-double-lane.png"></p>

We want to use this picture to explain specific components within the Cloud from a security perspective. We will start at the outside and work our way inwards.

#### 3.2.2 Cloud location

There are many regions within the AWS cloud where your cloud setup can be running. Examples of these regions are us-east-1, af-south-1, ap-northeast-1, EU-central-1.

As you can see in the picture, eMagiz cloud slots run within the EU-central-1 region. This region is located in Frankfurt and falls, therefore, under European data and security laws such as the GDPR.

#### 3.2.3 Cloud slot (VPC)

Within this region, a unique cloud slot per customer is assigned. This is represented as a Virtual Private Cloud (VPC) in the picture. Setting up a VPC provides a logically isolated section of the AWS Cloud where AWS resources can be launched in a virtual network explicitly defined for you. In addition, there is complete control over the virtual networking environment, including selecting the IP address range, creating subnets, and configuration of route tables and network gateways.

Incoming data from the internet passes through a load balancer to route data randomly to one of the core machines containing the runtimes holding the process flows. The setup of a VPC is governed by what we call a Cloud Template.

#### 3.2.4 Cloud template
 
This Cloud Template, designed by eMagiz, defines the setup of the cloud instance. The following parts of the cloud setup are configured here:

- Java version
- OS version (Linux)
- Runtime version
- Auto healing
- Monitoring
- Notification options

Making sure you are on the latest cloud template version guards yourself against vulnerabilities in older versions of Java and OS, for example. In addition, it gives the user more options for monitoring the health of the cloud environment reducing the risk of a loss of availability of data (promptly) without compromising the integrity of the data. For more information on what cloud templates are and how to control and update them, please check out this [microlearning](../microlearning/novice-emagiz-cloud-management-cloud-templates-explained.md).

#### 3.2.5 Carwash

All data exchanged between an external system and a cloud instance goes through the carwash that protects all client instances from harm and routes data to the correct client instance.

In terms of security, this means the following benefits from being behind the carwash:

- The connection is HTTPS instead of HTTP via the emagiz.com certificate
- Your VMs are protected because only the necessities that need to allow traffic let traffic through
- It gives you the ability to submit a certificate request via the Support portal to ensure two-way SSL (both server and client certificate validation).

### 3.3 Access to runtime / machine

In the last section, we looked at cloud-specific security measures. In this section, we take a step back and look at access to the runtime/machine that holds the process flows that process your data. As one can imagine, anyone with access to the machines where runtimes are running on can compromise the availability, integrity, and confidentiality of data. eMagiz offers two locations where eMagiz runtimes can be installed. Per location, specific security measures are discussed that should be taken to ensure the availability, integrity, and confidentiality of the data.

#### 3.3.1 On-premises

On-premises means that the runtimes are running on a machine outside the direct control of eMagiz. This means that the machine is running under the control of the customer within their IT landscape.

Because the machine is outside the direct scope of control of eMagiz, it becomes a joint effort between eMagiz and you as a customer to make sure that not everyone can access this machine. This becomes even more important when working with file-based actions as part of your integration. 
Advice would be to govern this via an IDP (i.e., Azure AD) so you can set up roles that have access to the machine or parts of the machine (i.e., some files).


##### 3.3.1.1 Rights for installing

To install a runtime on-premises, you need sufficient rights to execute (batch) programs. This means that the user needs administrator rights on that specific machine to perform the runtime installation correctly.

##### 3.3.1.2 Rights for running

In Windows, a service account is needed to run a Windows Service (in this case, the runtime you have installed). This service account is different compared to the user that does the installing of the runtime.
There are two options on this level:
    
- Use the local system account. This account has sufficient rights to run the service and can therefore be used for everything: less work to configure, more impact on data integrity when the account gets compromised.
- Use a specific service account per runtime, limiting the power of users to a particular runtime making you less vulnerable if this account gets compromised.

In Linux, the service will be running under the local system account as per default.

#### 3.3.2 Cloud

In the eMagiz Cloud, the access is restricted to those who have a legitimate reason to access it based on the SLA level agreements between customers and eMagiz. This means support engineers, consignment employees, and your model owner have access to your specific cloud setup.
This access is, per role, furthermore limited. This means that consignment employees and model owners can only see the logging of the runtimes on the machine and the ability to start/stop machines.

Support engineers can see more to analyze problems on a lower level.

All other users don't have access to the cloud setup as there is no need for access because they can perform the relevant actions on the Cloud via the eMagiz portal. For more information on how please see the [eMagiz Cloud Management](../microlearning/novice-emagiz-cloud-management-index) course.

##### 3.3.2.1 Rights for installing

To install a runtime in the Cloud, you need sufficient rights within the Deploy phase of eMagiz. We will later touch on portal rights on a model and phase level in this fundamental.

##### 3.3.2.2 Rights for running

The VPC in the Cloud runs on a Linux environment. Therefore the same logic applies as specified above for Linux systems. For example, in Linux, the service will run under the local system account as default.

### 3.4 Data encryption during transport

#### 3.4.1 Data "in transit"

As an integration provider, we transport data between applications. To ensure that the transport of this data is performed securely, several measurements have been taken to keep the information confidential.

Let us first look at the data "in transit." This is the process phase where data is interchanged between flows within the eMagiz platform. This data interchange goes (i.e., from entry to onramp or offramp to exit) via the orchestration of the JMS server on the messaging layer. This is nicely shown in the picture below.

<p align="center"><img src="../../img/fundamental/fundamental-emagiz-security-guide--data-orchestration.png"></p>

Data "in transit" is temporarily stored on an encrypted filesystem with the help of encryption algorithms. 
For the Cloud, eMagiz uses the AES-256 encryption algorithm. 
For on-premise runtime installations, eMagiz uses the AES-128 encryption algorithm. 
These algorithms ensure that even if third parties could get to the data on that encrypted filesystem, they won't be able to read the data.
That way, the data is kept confidential.

Above, we mentioned that data "in transit" is temporarily stored. This can happen in two places:

- On the JMS level (EFS)
- Before the message is placed on a queue (H2)

#### 3.4.2 Transport Layer Security

To ensure data integrity in the transport layer of eMagiz, it uses the TLS protocol. This means that all client-server communication is secured via TLS. In eMagiz, this is implemented as follows: The necessary certificates of the client(s) are trusted by the server, and the server is trusted by the client(s). The relevant information is stored in key stores and truststores that are unique per integration project (ll the integration configurations made to a single eMagiz instance spread across the ILM Phase from Capture to Manage). This ensures that data cannot be sent to other client projects or other environments within your project.
In other words, it prevents others from eavesdropping on your channels. eMagiz follows the standard guidelines when setting up TLS. Therefore, we ensure that the configured trusted certificate authority (CA) bundle that your messaging server uses to verify client connections is limited to only the CA used for your nodes, preferably an internally managed CA.

### 3.5 External data exchange 

Because eMagiz provides the integration between two or more applications via the eMagiz platform, the point at which the data is interchanged between application and integration is a critical part of the integration in terms of security.
Within eMagiz, there are three main integration patterns a user can configure to support their business case most optimally. First, this section will look at all three integration types in detail and specify the security measures.

#### 3.5.1 Messaging

Messaging is the most flexible option of the three; therefore, a wide range of options is available within eMagiz to secure the connections.
eMagiz offers users the tools to set up integrations and end-points in a secure manner. eMagiz supports well-known market standards, including:

- OpenID Connect
- WS-Security
- API Keys in combination with HTTPS/SSL
- SOAP Authentication
- OAuth2.0
- Basic Authentication
    
This way, each connection between the application and the integration (end-point) can be adequately secured and gives the flexibility to confer with the external application which method suits their needs the best. 

#### 3.5.2 API Gateway

A structure with roles and rights per role can be specified within the portal or via an external IDP to secure the front end of the API Gateway in eMagiz.

##### 3.5.2.1 Portal

As you can see in the picture shown below, the roles are defined so that the Read role can only access two integrations available for this specific API Gateway. If a client has insufficient rights, they will receive a 401 Unauthorized

<p align="center"><img src="../../img/fundamental/fundamental-emagiz-security-guide--api-gateway-portal-feedback.png"></p>

##### 3.5.2.2 External IDP

Apart from configuring the roles, users, and rights within the portal itself, it is also possible to hook the API Gateway up to an external IDP. 
By communicating with this IDP via the OAuth2.0 protocol, a check is done every time a client calls a specific operation to see whether that client has sufficient rights to access the operation. 
If the client has sufficient rights, the process continues. For example, if the client has insufficient rights, the client receives a 401 Unauthorized.

For the backend of the API Gateway, the same logic applies as stated above for messaging, which means that eMagiz supports the industry standard. Therefore, you as a user should confer with the external party about the correct method.

##### 3.5.2.3 Error handling

To prevent the error message if it occurs is sent straight back to the client, you can configure the front end of the API Gateway, so that correct HTTP Status codes are given back to the client, including a descriptive message.

 For more information on how this precisely can be configured via the eMagiz platform, please check the following [microlearning](../microlearning/crashcourse-api-gateway-configure-roles-and-users.md)

#### 3.5.3 Event Streaming

Within the Event Streaming solution, eMagiz provides Event Streaming users, and topics can be created.
Access to a topic within a cluster is governed by an Access Control List (ACL). This ACL links users to a topic and defines what the user can do on a topic (consume, produce, both).

Only users with sufficient rights in the Deploy phase of eMagiz can add users, topics and change the ACL entries specific to the Event Streaming cluster.

Apart from producing or consuming on specific topics based on the ACL, users also need to have a valid Keystore (containing the key and cert generated automatically) and a valid truststore (containing the CA certificate of the event streaming cluster) to produce or consume data.

These are all security measures to prevent third parties from getting unauthorized access to the data stored on the topics. 

For more information on how this precisely can be configured via the eMagiz platform, please check the following [microlearning](../microlearning/crashcourse-eventstreaming-user-management.md)

### 3.6 eMagiz iPaaS Portal

The eMagiz portal provides access to users to manage their eMagiz integration configurations. It provides access to all the features to develop, deploy and manage integrations across Test, Acceptance, and Production environments.

#### 3.6.1 Authentication & Authorization for ILM Phases

##### 3.6.1.1 User access to https://my.emagiz.com

Users can be added with their email address by the eMagiz Partner Manager, upon which the user gets an email to sign in. A temporary password is created and emailed, which has to be changed at the first login to the iPaaS portal. In addition, users are connected to organizations in eMagiz.
In the administration section of the user, an MFA token can be used to enable the Multifactor Authentication on a user level. Typical authenticators on a smartphone can be used, such as Google Authenticator. An MFA response is required for model owners to manage the permissions on a project level and any Edit activity in Production environments. See the following sections for more details on these functions.

##### 3.6.1.2 Users access to Integration Projects

Users can be added to Integration projects, which hold all the configurations required to run the different integrations for the TAP environments. Integration projects are connected to organizations in eMagiz to ensure the integration project remains within the limits of the license agreements. Users can be added to integration models by a model owner. Users can't be added to integration projects of other clients. 

##### 3.6.1.3 User authorizations to Integration projects.

Every integration project has a model owner who can distribute rights across functionalities and environments. The picture below shows the various options available across the Integration Life Cycle (ILM) Phases Capture through Manage. In addition, the model owner manages the user permissions and needs to have the MFA authentication level passed before making any changes. 
- When Edit permission is granted on an ILM phase, all the sub-options are configurable
- View rights mean that all options can be viewed only
- In case the user has no Edit or View rights to a specific ILM phase, the phase will not be displayed at all in the eMagiz iPaaS portal
- Model owners are assigned to integration projects by eMagiz Administrators
- An audit trail is kept of the changes made in the project permission structure

<p align="center"><img src="../../img/fundamental/fundamental-emagiz-security-guide--access-rights.png"></p>

##### 3.6.1.4 Partner user access to Client environments

Partner organizations are supported in eMagiz. Model owners can grant access to a model to their organization's users and affiliated organizations. On top of that, eMagiz administrators manage the connection between client and partners organization.

##### 3.6.1.5 Summary of relevant access to environments for eMagiz Administrators
eMagiz Administrators can view all integration projects and have model owner rights for all integration projects. 

##### 3.6.1.6 Password policy & Validity 
Below are relevant items for the password policy in the eMagiz portal.

- There is no expiry policy on the password - eMagiz has a Forget Password functionality. 
- Password must be 8 - 20 characters long, cannot contain white spaces, and must contain at least one digit, one upper case, and one lower case letter."

#### 3.6.2 Integration project versioning & audit trails

- In all the relevant parts of the integration project, developers can version the changes made. The type (major, minor, or patch) can be indicated and commented on to describe the change. Once the version is created, that particular version will be available for Deployment and is then kept in the history of changes on a low level. Both are illustrated in the pictures below.

<p align="center"><img src="../../img/fundamental/fundamental-emagiz-security-guide--create-new-version.png"></p>

<p align="center"><img src="../../img/fundamental/fundamental-emagiz-security-guide--history-pages.png"></p>

- On a CDM level, the same functionality exists to indicate the version type incl. comments. All changes to the CDM model are logged in an audit trail that can help understand what changes are made by who in case of error resolution. The CDM is also protected by the permission structure of the Integration project.

- In Design, the required architecture of the different eMagiz components can be created. An audit trail is kept to see who has made what change, so actual realization issues of this architecture can be resolved faster. For example, in Deploy, the architecture is implemented to the Cloud, and a similar audit trail is kept there.

#### 3.6.3 eMagiz Monitoring capabilities & Security features

Monitoring your (Production) environment helps you monitor and detect deviations within your environment in near real-time. The ILM phase Manage provides access to errors logs generated in message processing by the platform and monitoring logs of the Cloud components and eMagiz runtimes. All errors and relevant logging is stored for a limited period (two weeks) within eMagiz for auditing or reporting purposes. Furthermore, notifications can be sent to people to alert them of a potential loss of data integrity. These alerts can contain a warning or the actual error that occurred. 

If specific messages are processed but result in validation errors or other errors, the message is sent to the error stack. The developer can view the actual message, including the content, to understand the error reported adequately. For example, the eMagiz store holds a specific transformation (Mask XSLT) that can mask all the fields of the XML message sent to the error stack. It can mask all the fields or only specific fields that contain sensitive data. Clients are requested to make this assessment per integration advised by the eMagiz Partner. In future versions of eMagiz, particular attributes of entities in System Messages or CDM messages can be flagged, so the platform automatically takes care of this feature.

### 3.7 GDPR compliancy

Our privacy policy is mentioned on this page: https://www.emagiz.com/privacy-policy/. The eMagiz platform holds for registered users only the username and password. The user name is the company email address, and no other data is kept on a personal user level. 

The eMagiz portal at https://my.emagiz.com does not store any cookies. Instead, there are functional items only kept in the user's session data once active in the eMagiz portal. Specific logs are created in the eMagiz portal that displays operational issues a user has in using the portal. These logs are only viewable by eMagiz users and contain no personal data.

### 3.8 Data retention  
eMagiz stores specific integration scenario data. Within the basic configuration, eMagiz only processes the data and doesn't keep any data from these message streams. All messages are treated the same way, and the platform doesn't distinguish between regular, personal, or sensitive data. Clients are requested to make such assessments and take precautionary measures. Below we have detailed the parts of the eMagiz offering, per integration pattern, in which data is held temporarily. Afterward, we turn our focus to our data management offerings in which we store data for a longer period to support the client's needs.

#### 3.8.1 Messaging

In the integrations where the Messaging pattern is selected, the entry connectors (runtimes that receive or pull messages) are equipped with a small temporary database to ensure the letters are preserved in this phase. In case of brief downtime of consecutive components where these messages are processed, these messages are held. This is one part of the Guaranteed Delivery mechanism in eMagiz. Messages are encrypted (AES-128) and stored until the message is processed - the database can only be thoroughly cleaned if needed by removing the data file of this database. Only users that have sufficient permissions can restart. Depending on input received and throughput achieved by polling the database, this can range between seconds and minutes that a message is kept in the database.

The eMagiz JMS component manages the queues between the different steps in the integration flow. All data within these queues are encrypted via an encryption algorithm (AES-256), and data will only be retained here until the next step in the process is ready to consume the data.

#### 3.8.2 Event Streaming

In the case of event streaming, data is temporarily kept on the topic within the event streaming cluster. As specified above, access to a topic is secured with the help of the ACL. This is a safeguard against a loss of integrity of data. Regarding Event Streaming, data is retained for a more extended period (often days) to ensure that consumers have sufficient time to consume the data before it is deleted. This does mean that unauthorized third parties can not easily access the data on these topics. In addition, authorized users can edit the retention size and retention times on the topic level.

- Service instances and the underlying VMs use full volume encryption using LUKS with a randomly generated ephemeral key per each instance and volume. The key is never re-used and will be trashed at the destruction of the instance, so there's a natural key rotation with roll-forward upgrades. We use the LUKS default mode aes-xts-plain64:sha256 with a 512-bit key.
- Backups are encrypted with a randomly generated key per file. These keys are encrypted with RSA key-encryption key-pair and stored in the header section of each backup segment. The file encryption is performed with AES-256 in CTR mode with HMAC-SHA256 for integrity protection. The RSA key pair is randomly generated for each service. The key lengths are 256-bit for block encryption, 512-bit for integrity protection, and 3072-bits for the RSA key. 
- These backup files are stored in the object storage in the same region where the service virtual machines are located.


#### 3.8.3 API Gateway

At this moment, there is no data stored in eMagiz API Gateways configurations. Instead, backend flows that connect to the APIs being called use the same queuing mechanism as mentioned in the previous section around Messaging.

#### 3.8.4 Data management

For more information on the conceptual ideas behind data management within the eMagiz platform, you can look at this [fundamental](fundamental-data-management.md). For more concrete information on how to implement it within an eMagiz flow you could check out this [microlearning](../microlearning/advanced-data-management-data-sink.md) and this [microlearning](../microlearning/advanced-data-management-long-term-archiving.md). All the information within the data sink and the long-term archiving solution is kept within the same VPC in the Cloud and can only be accessed by authorized parties.

### 3.9 Compliancy

- eMagiz has the ISO-27001 certification at this moment.

### 3.10 Other

#### 3.10.1 Penetration testing

eMagiz services are periodically assessed and penetration tested by an independent pentesting supplier for any security issues.

During these tests, the pentester will try to achieve goals (penetration of the target system on various levels) by undertaking various means. Such a test can help determine whether a system is vulnerable to attack if the defenses were sufficient and which defenses (if any) the test defeated. In addition, eventual findings from those tests are dealt with conforming to the corrective action processes in our ISMS.

##### Practice

## 4. Key takeaways

- Protecting your data is a joint responsibility between eMagiz and you
- The repository is read-only for clients
- Data in the Cloud is kept within your VPC
- Production data in the portal is behind an MFA check

</div>
</main>
</div>
</div>