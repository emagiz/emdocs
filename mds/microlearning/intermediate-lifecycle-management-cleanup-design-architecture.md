<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-lifecycle-management-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Cleanup a designed integration
 
In this microlearning, we will focus on the second to last step of cleaning up your integration. As we learned in previous microlearnings the lifecycle management process starts in Manage and ends in Capture. Following that logic, the second to last step of the process is to clean up your designed integration.

Should you have any questions, please contact academy@emagiz.com.

- Last update: May 14th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Basic knowledge of the build number component within the eMagiz Platform

## 2. Key concepts
This microlearning centers around cleaning up a designed integration.

By designed integration we mean: A line that symbolizes data traffic between a system and eMagiz for which the solution is designed (i.e. message definition, message mapping, design settings)

There are four key considerations before cleaning up a captured integration:

- Is the integration/flow not mentioned anymore in any alerting in Manage?
- Is the integration removed from all releases?
- Is the integration removed from Create?
- What should I clean up in Design that is not automatically done when I cleanup Capture?

##### Theory
  
## 3. Cleanup a designed integration

In this microlearning, we will focus on the second to last step of cleaning up your integration. As we learned in previous microlearnings the lifecycle management process starts in Manage and ends in Capture. Following that logic, the second to last step of the process is to clean up your designed integration.

There are four key considerations before cleaning up a captured integration:

- Is the integration/flow not mentioned anymore in any alerting in Manage?
- Is the integration removed from all releases?
- Is the integration removed from Create?
- What should I clean up in Design that is not automatically done when I cleanup Capture?

As you can see a theme starts to develop itself. Each of the considerations focuses on a particular phase within eMagiz. We start at Manage, move to Deploy, Create and Design before we end up in Capture. Doing this properly will ensure that the deletion of the integration and everything that accompanies it will be successful.

Good to know is that most in Design will automatically be removed when you clean up the captured integration. More on the specifics of  that in the next microlearning ([Cleanup a captured integration](novice-lifecycle-management-cleanup-a-captured-integration.md)). For now, it is good to know that the CDM is untouched by that action. That means to ensure a proper cleanup you should verify if certain elements in the CDM are not used anymore and are therefore ready to be cleaned up.

To do so you can search on CDM level for unused parts of the CDM. When you have identified them you can remove them. We will discuss this topic in more detail later on in [Cleaning up the CDM](intermediate-defining-your-message-structures-cleaning-up-the-cdm.md). So before you will do this in a real project take stock of that microlearning.

For this microlearning, it is good to know that apart from the CDM everything in Designed will be cleaned up when you clean up the captured integration.

##### Practice

## 4. Assignment

Determine whether a designed integration within your project can be cleaned up. If so read the microlearning [Cleaning up the CDM](intermediate-defining-your-message-structures-cleaning-up-the-cdm.md).
This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- There are four key considerations before cleaning up a captured integration:
    - Is the integration/flow not mentioned anymore in any alerting in Manage?
    - Is the integration removed from all releases?
    - Is the integration removed from Create?
    - What should I clean up in Design that is not automatically done when I cleanup Capture?
- Before deletion eMagiz will ask for confirmation
- Deletion means that you cannot get it back anymore
- The process of removing parts of the CDM will be discussed in more detail later on.

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the release notes provided by eMagiz

## 7. Silent demonstration video

As this is a more theoretical microlearning we have no video for this

</div>
</main>
</div>
</div>