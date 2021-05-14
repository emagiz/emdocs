<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/novice-lifecycle-management-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Cleanup a captured integration
 
In this microlearning, we will focus on the last step of cleaning up your integration. As we learned in previous microlearnings the lifecycle management process starts in Manage and ends in Capture. Following that logic, the last step of the process is to remove the integration from Capture (and potentially the system)

Should you have any questions, please contact academy@emagiz.com.

- Last update: April 22th, 2021
- Required reading time: 7 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Basic knowledge of the build number component within the eMagiz Platform

## 2. Key concepts
This microlearning centers around cleaning up a captured integration.

By captured integration we mean: A line that symbolizes data traffic between a system and eMagiz for which the specific information is filled in (i.e. captured)

There are four key considerations before cleaning up a captured integration:

- Is the integration/flow not mentioned anymore in any alerting in Manage?
- Is the integration removed from all releases?
- Is the integration removed from Create?
- Is the eMagiz data model (i.e. CDM, API Gateway Data model) cleaned?

##### Theory
  
## 3. Cleanup a captured integration

In this microlearning, we will focus on the last step of cleaning up your integration. As we learned in previous microlearnings the lifecycle management process starts in Manage and ends in Capture. Following that logic, the last step of the process is to remove the integration from Capture (and potentially the system)

There are four key considerations before cleaning up a captured integration:

- Is the integration/flow not mentioned anymore in any alerting in Manage?
- Is the integration removed from all releases?
- Is the integration removed from Create?
- Is the eMagiz data model (i.e. CDM, API Gateway Data model) cleaned?

As you can see a theme starts to develop itself. Each of the considerations focuses on a particular phase within eMagiz. We start at Manage, move to Deploy, Create and Design before we end up in Capture. Doing this properly will ensure that the deletion of the integration and everything that accompanies it will be successfully deleted.

However, there is no check done on all these aspects when you want to delete the integration. Therefore it is up to you to uphold the quality. There is one exception to this and that is the fact that the integration needs to be removed from Create before you can clean it up (i.e. delete) in Capture. If the integration is not yet removed from Create you will see the following pop-up:

<p align="center"><img src="../../img/microlearning/novice-lifecycle-management-cleanup-a-captured-integration--not-able-to-remove.png"></p>

To remove an integration in Create simply access the context menu (via a right-mouse click) and select the option Delete integration.

<p align="center"><img src="../../img/microlearning/novice-lifecycle-management-cleanup-a-captured-integration--delete-integration.png"></p>

When selecting this option eMagiz will ask for confirmation to make sure that you know what you are doing. Confirming that you want to delete the integration means that you throw away all captured information including attached documents. Furthermore, it means that all message mappings, system messages, and design configurations are also gone, except for entities and attributes on the CDM level as they are shared.

In cases where the integration you have just cleaned up is the last integration tying a system to eMagiz, you should also delete the system itself. This can be achieved similarly. On the system level, you can access the context menu and select the option Delete system. 

<p align="center"><img src="../../img/microlearning/novice-lifecycle-management-cleanup-a-captured-integration--delete-system.png"></p>

Once again you will receive a confirmation pop-up. Confirming, in this case, means deleting all captured information on the system level and removing all designed information on the system level.

Armed with this knowledge you can make the correct decision in cases where you consider cleaning up the captured integration.

##### Practice

## 4. Assignment

Determine whether a captured integration within your project can be cleaned up. If so execute the clean-up.
This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- There are four key considerations before cleaning up a captured integration:
    - Is the integration/flow not mentioned anymore in any alerting in Manage?
    - Is the integration removed from all releases?
    - Is the integration removed from Create?
    - Is the eMagiz data model (i.e. CDM, API Gateway Data model) cleaned?
- Before deletion eMagiz will ask for confirmation
- Deletion means that you cannot get it back anymore

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the release notes provided by eMagiz

## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned. 

<iframe width="1280" height="720" src="../../vid/microlearning/novice-lifecycle-management-cleanup-a-captured-integration.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
</main>
</div>
</div>