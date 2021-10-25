<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-solution-architecture-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

#####Intro

# Introduction
This micro-learning will focus on some considerations for putting the eMagiz runtime at the right location in the architecture. 

Should you have any questions, please contact academy@emagiz.com.

- Last update: October 20th, 2021
- Required reading time: 10 minutes

## 1. Prerequisites
- Intermediate knowledge of the eMagiz platform
- Good working experience in the Design and Deploy Architecture phase.

## 2. Key concepts
In the various microlearnings until the intermediate level, we have explained the eMagiz runtime (https://emagiz.github.io/docs/microlearning/crashcourse-platform-deploy-install-local-connector). In short, it is the process that can make the flow components operational and execute the designated tasks of that flow. Please refer to these microlearnings for further information

##### Theory

## 3. Specific eMagiz runtime considerations 

###3.1 Messaging pattern runtimes
For Messaging specific patterns the runtime should be place in such a way that there is connectivity between that runtime and the sending / receiving system. The system might be located in a Cloud service, or Cloud VPC that eMagiz clients are hosting. Or are located on-premises of the client. Here are the options and advices for putting the runtime.

1. Sender or Receiver system is located in a public or private Cloud
	- Put the Runtime on a Cloud Connector machine and ensure to use the connectivity options provided in eMagiz
	
2. Sender or Receiver system is located in a DMZ section of the client infrastructure
	- Put the runtime inside the same DMZ zone to keep the runtime as close to the system as possible
	- Ensure the management of the runtime is something workable for the client. Consider the updates that may occur as well as the fact that the runtime can no longer be managed by the eMagiz Portal
	
###3.2 API Gateway pattern runtimes
For these runtime the first choice is put all the Gateway Entry Flow and the Exit gates on the Cloud Connector machine. This way, the number of runtimes are kept to a minimum and there is full control over these runtime. In the exceptional case where the exit gate needs to connect to a system that is not accessible via the client firewalls, you can opt to put these exit gates only on a runtime that can be deployed on-premises. Please refer to the [microlearning around running part of the solution locally](advanced-api-management-running-part-of-your-api-gateway-solution-on-premise)

###3.3 Event Streaming pattern runtimes
In the case where Event processors are used in the Event Streaming solution designed, eMagiz provides a event streaming container (runtime). This runtime can only run in a Cloud based machine, and only in the core machines of eMagiz. The key reason is that these Event Processors need to connect to the topics that are only available in the eMagiz Cloud and not accessible from outside the eMagiz VPC. Any runtime that is consuming or producing data with these topics needs to have the capability to access such topics. 


##### Practice

## 4. Assignment

There is no specific assignment as this is more theoretical microlearning.

## 5. Key takeaways
Take into account the key considerations for each case to ensure the runtime is placed on the right location. 

##### Solution

## 6. Suggested Additional Readings

There are no suggested additional readings on this topic

## 7. Silent demonstration video

There is no demonstration video of this functionality. 

##

</div>
</main>
</div>
</div>