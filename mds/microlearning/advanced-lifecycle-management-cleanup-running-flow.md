<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-lifecycle-management-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

#####Intro

# Cleanup a running flow 
 
In this microlearning, we will focus on the part of the lifecycle management where you need to clean up a flow that is active on a runtime at the moment when the integration needs to be removed. It involves complexity in a sense that flow needs to be removed from the Deploy phase. Before it can be removed from the Create phase and further.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: August 27th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
-

## 2. Key concepts
The most important for this micro-learning to understand is that a flow needs be removed from the Deploy phase before it can be removed from the integration model that is in Capture, Design and Create. Removing a flow from the model before removing it from Deploy results in "ghost" flows that result in unexpected behavior in the Deploy phases.

##### Theory
  
## 3. Steps to remove a flow from Deploy


###3.1 Remove from runtimes

1. Stop the flow from the runtime where its active. Remove on all runtimes where it is active
2. Uninstall the flow from the runtime(s) where it was active
3. Update the Container assignment to remove the flow from the Containers

###3.2 Remove unused Properties
Ensure to remove the associated properties from each TAP environment specific to this flow. Refer to the micro-learning that explains that process.

###3.3 Remove alerting triggers

Within this Tab navigate to Triggers (look at the Tag name when following these instructions). If you have configured the alerting following the best practice outlined in the user guide for Alerting, the following triggers (at least!!!) need to be changed. For your specific situation more triggers could be relevant
- Standard – Queue consumers too high
- Standard – Queue consumers too low

If you are removing the last flow belonging to a system and you have followed the best practice outlined here the following triggers (at least!!!) need to be changed. For your specific situation more triggers could be relevant

- Standard – Data measurements missing
- Standard – Log entries missing
- Standard – Error log entry

###3.4 Remove from all Releases
The key to understand is that the flow to be removed needs to be removed from all the releases in the 3 environments test, acceptance and production. In most cases, it means that a new (series of) release(s) needs to be created and made active in each environment. Older releases can be removed so that no release has this flow included. Once that is achieved, then the flow is removed from the Deploy phase. 

It usually means that it will take a certain grace period before a flow is actually out of Deploy.


##### Practice

## 4. Assignment

Determine whether you can clean up a deployed flow within your project. If so, execute the cleanup from Deploy as displayed above. This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- A flow needs to be removed from all releases before it can be removed from Create - see specific micro-learning for that purpose
- Don't forget to clean the Manage phase with Alert triggers, and the properties from Deploy

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it, please read the release notes provided by eMagiz

## 7. Silent demonstration video

There is no specific video - the steps above include sufficient information for now.

</div>
</main>
</div>
</div>