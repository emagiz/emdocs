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


# Cleanup Alerting in Manage
 
In this microlearning, we'll take a look how to cleanup Alerting from an eMagiz project.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: August 25th, 2021
- Required reading time: 2 minutes

## 1. Prerequisites
- Novice knowledge of the eMagiz platform

## 2. Key concepts
This microlearning is about cleaning up the Alerting as configured in the Manage phase. Alerts can be set on various ways and levels - please inspect the related microlearnings around alerting to understand more about that. During the cleanup of various systems, flows and runtime, the Alerting needs to remain current with the integration model. 

##### Theory
  
## 3. Cleanup the Alerting in Manage

### 3.1 Scenario's when to cleanup the Alerting phase

1. A user is no longer active on the integration model. The use may still be referenced in the notification settings and should be removed
2. A specific runtime is removed from the integration model that is referenced in the Alerting
3. A flow or integration is removed from the integration model that is reference in the Alerting

### 3.1 Steps to clean

Navigate to the Triggers first.

1. Locate Queue specific
If you have configured the alerting following the best practice outlined in the user guide for Alerting, the following triggers (at least!!!) need to be changed. For your specific situation more triggers could be relevant
- Standard – Queue consumers too high
- Standard – Queue consumers too low

2. Locate Runtime specific
If you are removing the last flow belonging to a system and you have followed the best practice outlined here the following triggers (at least!!!) need to be changed. For your specific situation more triggers could be relevant
- Standard – Data measurements missing
- Standard – Log entries missing
- Standard – Error log entry

3. Once you have located the candidates, update and/or remove the triggers relevant for update
4. Review if you need to remove a notification setting in case a trigger is removed. If yes, remove it.
5. Review if you need to remove a tag in case the tag is not used in any trigger. If yes, remove it.


##### Practice

## 4. Assignment


Determine whether you can clean up parts of the Alerts from the project that you work on. If so, execute the cleanup.
This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Cleaning up the Alert phase is important to ensure no false positive alerts are created/used
- Review the Alert setting at each release to production (post deployment step) to keep things manageable

##### Solution

## 6. Suggested Additional Readings

None

## 7. Silent demonstration video

None

</div>
</main>
</div>
</div>