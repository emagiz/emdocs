<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/novice-emagiz-cloud-management-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# eMagiz Cloud Management - Introduction

In the remainder of this course and other courses surrounding the topic of eMagiz Cloud Management managing the eMagiz Cloud is a central topic. The main idea of having the ability to control the eMagiz Cloud from the eMagiz portal is to increase what a user can do without the help of experts that master the specific Cloud environment where the eMagiz instance is deployed (in this case AWS). 

Should you have any questions, please contact academy@emagiz.com.

- Last update: May 27th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around introducing eMagiz Cloud Management
With eMagiz Cloud Management, we mean: Having the ability to control the eMagiz Cloud from the eMagiz portal.

To summarize, controlling the eMagiz Cloud gives you:
-   Tools to stay in control of the eMagiz Cloud.
-   A way to do it yourself.

##### Theory

## 3. eMagiz Cloud Management - Introduction

In the remainder of this course and other courses surrounding the topic of eMagiz Cloud Management managing the eMagiz Cloud is a central topic. The main idea of having the ability to control the eMagiz Cloud from the eMagiz portal is to increase what a user can do without the help of experts that master the specific Cloud environment where the eMagiz instance is deployed (in this case AWS). 

This functionality enables users to make the following configuration changes to the eMagiz Cloud
- Upgrade Cloud Template
- Start / Stop Runtimes
- Start / Stop Machines
- Add / Remove Runtimes
- Add / Update Routes
- Add / Update Certificates
- Reset Runtime
- Clean Store
- Slot Standby / Slot wakeup
- Mendix stand by connector
- Fixed IP

In the remainder of this course, we will focus on the first three actions. Before we delve into the specific actions let us first take a broader perspective and look at the best practices when managing the eMagiz Cloud

### 3.1 Best practices

-   Read the release notes on the eMagiz portal every time a new cloud template is released by eMagiz. These release notes can be found under Documentation -> Release Notes -> Cloud Templates
-   Keep your Cloud setup as up to date as possible
-   When using the Slot Standby / Slot Wakeup functionality combine this with the 'Mendix stand by connector' to prevent a large number of errors/warnings in the log 
-   All actions described below can only be executed on AWS cloud environments and AWS cloud runtimes
-   If you are unsure what a certain action does, please discuss the steps you want to make with someone else before executing them, use the Q&A section in the eMagiz Portal, or contact productmanagement@emagiz.com
-   All changes made from the eMagiz Portal are only sent to the AWS cloud when the eMagiz platform sends out the command. Per functionality, it differs when the action is sent.
-   In the case of a so-called double lane bus (failover available) you have the option to first update the failover setup (Availability Zone B) and at a later stage the ‘live’ setup (Availability Zone A). This to prevent downtime of the platform instance

##### Practice

## 4. Assignment

There is no assignment for this microlearning.

## 5. Key takeaways

-   Tools to stay in control of the eMagiz Cloud.
-   A way to do it yourself.

##### Solution

## 6. Suggested Additional Readings

There are no suggested additional readings on this topic

## 7. Silent demonstration video

There is no demonstration video of this functionality. 

</div>
</main>
</div>
</div>