<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-solution-architecture-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Understanding Design Architecture
 
In a previous microlearning on this [subject](crashcourse-platform-design-understanding-design-architecture-basic.md) we have learned the basics of the Design Architecture overview. In this microlearning, we will expand our knowledge of Design Architecture. This is to get an even better understanding of what the Design Architecture overview is about and how you can best utilize this within the context of your project(s). Having this knowledge will make it easier to make a correct architectural decision in the long haul.

Should you have any questions, please contact academy@emagiz.com.

- Last update: July 27th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on understanding design architecture.

With Design Architecture we mean: The desired overview of where the instances are deployed, on which machines, and how many resources it takes to deploy these instances

The focal point of this microlearning will be to provide context on the Design Architecture page:

- Approval (Cloud, Topic Storage, etc.)
- Ratio between size and number of runtimes (Golden ratio)
- Impact / Consequence of changing something in Design Architecture
- Why do Design and Deploy Architecture differ from each other (in some cases)

##### Theory
  
## 3. Understanding Design Architecture

In a previous microlearning on this [subject](crashcourse-platform-design-understanding-design-architecture-basic.md) we have learned the basics of the Design Architecture overview. In this microlearning, we will expand our knowledge of Design Architecture. This is to get an even better understanding of what the Design Architecture overview is about and how you can best utilize this within the context of your project(s). Having this knowledge will make it easier to make a correct architectural decision in the long haul.

The focal point of this microlearning will be to provide context on the Design Architecture page:

- Approval (Cloud, Topic Storage, etc.)
- Ratio between size and number of runtimes (Golden ratio)
- Impact / Consequence of changing something in Design Architecture
- Why do Design and Deploy Architecture differ from each other (in some cases)

### 3.1 Approval

The first point of attention is the approval process. As deploying your integration data model to the cloud will cost resources there needs to be an approval process to ensure that you as a customer have the right to use a certain amount of cloud resources. The same applies to when you would use the Event Streaming pattern and want to increase (or decrease) the amount of topic storage you are contractually allowed to use.

To get approval a contractual agreement needs to be struck between you as a customer and eMagiz. This contractual agreement could be struck via a partner construction. To start the approval process it is best to contact the person with whom you have the most contact when it comes to the eMagiz platform (in most cases your partner manager). They will then ensure that the request is communicated to the proper authorities for approval.

After the contract is signed and the increase (or decrease) of Cloud and/or Topic Storage is configured you will be notified that the approval has succeeded. At this point, you can continue expanding your integration data model.

### 3.2 Golden Ratio

The runtime is the component into which the individual integration flows are deployed. It's a Java-based application container that can run in the Cloud or Local. A runtime is visually displayed and described in the eMagiz iPaaS Portal as a process container (holding the onramps, offramps, routing, error), an event streaming container (holding the event processors), a gateway container (holding all entry and the exit gates), or a connector (holding the exits and entries).

One critical element in Design Architecture is determining how many runtimes can run on a specific machine. For a detailed explanation on that, I would like to refer you to the following [microlearning](expert-solution-architecture-determining-needed-memory.md). As a general rule of thumb, we use a placeholder of 1GB of memory per runtime. That means that roughly speaking you can safely place 8 runtimes on an L machine. You will notice that when you dig into the numbers deeper the number can shift based on the actual implementation.

### 3.3 Impact of changes

In theory, changing anything in Design Architecture has no direct impact. In practice, however, it is good to be aware of the potential consequence. Imagine the following scenario, you and a few other colleagues are working within the same integration data model. You are currently moving around runtimes with the intent of actualizing that change one week later. However, in the meantime, a colleague of yours needs to expand the integration data model that is running on the cloud with a new runtime. As you all are working in the same integration data model eMagiz will actualize **all** changes when your colleague presses Apply to Environment in Deploy Architecture. So be aware of when you change things and when you do ensure to communicate with all stakeholders related to the project how you plan to actualize those changes.


### 3.4 Design vs Deploy Architecture

In the previous segment, we talked about the impact of changing things in Design Architecture. In this segment, we will look at some scenarios in which the Design Architecture view can differ from the Deploy Architecture view. There are three main reasons why both of them differ:

- This is the first time you open Deploy Architecture
    - This means you need to spin up your cloud infrastructure for the first time
- There is no flow related to the runtime embedded in the release
    - Runtimes won't show up in Deploy Architecture when no flow should be deployed on them within the currently active release
    - Note that this can differ per environment
- The runtime is excluded in Design Architecture
    - With this functionality, you explicitly mention that a certain runtime should not be deployed

Knowing this should make you better equipped to handle 'unexpected' situations you occur while implementing your data model with the help of the eMagiz platform.

##### Practice

## 4. Assignment

Read up on the release notes of the various platform components and determine for the projects in which you operate what the status is of your eMagiz solution on the eMagiz platform.

## 5. Key takeaways

- Key considerations when dealing with Design Architecture are:
    - Approval (Cloud, Topic Storage, etc.)
    - Ratio between size and number of runtimes (Golden ratio)
    - Impact / Consequence of changing something in Design Architecture
    - Why do Design and Deploy Architecture differ from each other (in some cases)

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help texts provided by eMagiz

## 7. Silent demonstration video

As this is a more theoretical microlearning we have no video for this

</div>
</main>
</div>
</div>