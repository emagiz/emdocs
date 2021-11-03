<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-cloudmanagement-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>
<div class="doc">
 
##### Intro

# Impact of Cloud template upgrades
 
In this microlearning, we will focus on the helping you to assess the impact of upgrading to a new Cloud template.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: November 2nd, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- Completed the relevant microlearnings around Cloud Management till advanced.


## 2. Key concepts
With cloud template, we mean: A Cloud template is a configuration, specified by eMagiz, how deploy Architecture will run in AWS, and which supporting tools (such as auto-healing, auto-recovery, and improved alerting for instance) are available for your environment.

Cloud Templates:
- Determine what runtime runs where
- Determine which eMagiz Cloud version will we use
- Determine which supporting tools are available
- Are updateable

##### Theory
  
## 3. Assessing the impact of upgrading Cloud templates

The following consideration are valid when upgrading to a new Cloud template

1. Service affecting vs. non-service effecting
Non-service affecting templates will not affect your current operation - flows will continue to function as usual. You can safely apply the cloud template. Service affecting means that that the machines will need to be stopped and started to make the cloud template operational. There is short window in which flows are not operational and there will be a delay in message delivery & processing. Messages is not lost.

2. Other changes pending for an AWS update
The apply to environment button will apply all the changes that are made in Design architecture and Deploy architecture. These can be things such as 

- Memory changes
- Runtimes removed
- Runtimes added
- Etc.

It is a good practice to isolate the Cloud template upgrade from these changes to the AWS slot. All changes can be handled in a single push of the button, but when an issue occurs at that moment it may become harder to isolate the root cause. So keep your Deploy Architecture as current as possible.
 

3. Duration of the upgrade
A Cloud template upgrade will take between 5 and 15 minutes depending on the size of the slot in terms of machines. Take this value into account when making the plan to upgrade or set the automatic upgrade timeslot.

4. Availability zone
For fail-over setups, the Cloud template upgrade will perform the upgrade zone by zone. There are 2 zones (A and B) defined in the failover scenario. Effectively this means that there is no downtime in the entire environment as flows and the JMS server will continue to operate as usual.

5. Multiple Cloud template upgrades
In case you have a backlog of upgrades to perform, please take each cloud template step by step. In case you switch to an automatic upgrade, this upgrade will take of making all the upgrades.


##### Practice

## 4. Assignment

Review the release notes in the Portal, be sure to understand the release notes of each cloud template. And which are service affecting and which ones not.

## 5. Key takeaways

- Cloud templates can be rolled-out automatically via the upgrade options. Regardless of the type of environment (Test, Acceptance or Production)
- Double lane Cloud template upgrades are non-service affecting.
- Make sure to keep your Deploy architecture current - less risk of impact of Cloud template upgrade issues.

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it, please read the release notes provided by eMagiz

## 7. Silent demonstration video

There is no video available as this is more a theoretical microlearning.

</div>
</main>
</div>
</div>