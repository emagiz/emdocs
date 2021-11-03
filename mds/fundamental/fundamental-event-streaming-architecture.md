<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/fundamental/index_academy_fundamental_event-streaming" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>
<div class="doc">
 
##### Intro

# eMagiz Event Streaming - Architecture
 
In this microlearning, we will introduce the most important concepts of the Event Streaming architecture in eMagiz

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: November 3rd 2021
- Required reading time: 8 minutes

## 1. Prerequisites
- Completed the crashcourses of eMagiz
- Completed the fundamental - Event Streaming Introduction

## 2. Key concepts
Please refer to the introduction microlearning of this fundamental to understand all concepts.

##### Theory
  
## 3. Architectural components of Event Streaming in eMagiz

A simplied picture below is list to illustrate the overall architecture of Event Streaming in eMagiz.

<p align="center"><img src="../../img/howto/fundamental-event-streaming-architecture-1.png"></p>

### 3.1 Event Broker
eMagiz is hosting an Event Broker inside the eMagiz Cloud and is accessible only via the eMagiz platform. All traffic is routed via the eMagiz platform, and is protected 2-way SSL. The Broker holds the specific Kafka based technology around managing topic, Access Control Lists (ACL), users, retention, etc. All components as decribed in the introduction section of this Fundamental. The broker will respond to the requests made from the eMagiz platform such as putting a message on topic and soforth.

### 3.2 eMagiz Platform
The iPaaS platform provides access point where external users can put their produce and consume requests in. The eMagiz iPaaS portal manages the configuration if the Event Streaming broker via the eMagiz platform. For instance the retention settings are set in the eMagiz iPaas Portal and then effectuated in the Event Broker.

### 3.3 JMS and Event Streaming container
In the case where specific flows are deployed for Event Processing, the regular JMS server will control and manage the traffic. The Event Streaming Container will hold the required flows for Event Processors. The Core machine is not accessible from outside the VPC - as usual for the eMagiz core machine.

### 3.4 Users
Users will have access to produce and consume messages. Users are managed in User Management sections in the eMagiz Portal. Once configured, the credentials are accessible via the Event Catalog. Users can access the topics via SSL and certificates. The Key and Trust stores are available in the Event Catalog - as well as all the required details of the Event Broker to allow access. Other access methods such as Basic Authentication, SASL like options are not supported to access the Event Broker.



##### Practice

## 4. Assignment

There is no specific assigmment here. Please review the Use case for Event streaming more closely to learn more about the configuration in eMagiz.

## 5. Key takeaways

- Please review the architecture carefully

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it, please read the use case around Event Processing in the Use Cases section of the eMagiz Academy section.

## 7. Silent demonstration video

There is no video available as this is more a theoretical microlearning.

</div>
</main>
</div>
</div>