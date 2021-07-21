<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-emagiz-cloud-management-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Apply to environment

In this microlearning, we will focus on the "apply to environment" action. As we saw in previous microlearnings and will see in microlearnings to come with regards to cloud management is that some actions in Deploy Architecture have a direct effect (i.e. Slot Wakeup, Restart Runtime, Reset Runtime, etc.) and others have an indirect effect (i.e. Add Route, Add Certificate, Remove Runtime, etc.). For the actions that have an indirect effect on the eMagiz Cloud, you need the "apply to environment" functionality to actualize the changes on the eMagiz Cloud level.

Should you have any questions, please contact academy@emagiz.com.

- Last update: July 21th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Basic knowledge of cloud management

## 2. Key concepts
This microlearning centers around the apply to environment action
With "apply to environment", we mean: Actualizing all changes, with an indirect effect, within the eMagiz Cloud that were made by users on the Deploy Architecture canvas after the last press on this button

- Apply to environment actualizes all changes with an indirect effect
- It gives you the option to change multiple things at once before applying the bulk change. This is to reduce downtime
- It ensures that the eMagiz Cloud is only affected when a user want to affect it

##### Theory

## 3. Apply to environment

In this microlearning, we will focus on the "apply to environment" action. As we saw in previous microlearnings and will see in microlearnings to come with regards to cloud management is that some actions in Deploy Architecture have a direct effect (i.e. Slot Wakeup, Restart Runtime, Reset Runtime, etc.) and others have an indirect effect (i.e. Add Route, Add Certificate, Remove Runtime, etc.). For the actions that have an indirect effect on the eMagiz Cloud you need the "apply to environment" functionality to actualize the changes on the eMagiz Cloud level.

The Apply to environment functionality gives you:
- Apply to environment actualizes all changes with an indirect effect
- It gives you the option to change multiple things at once before applying the bulk change. This is to reduce downtime
- It ensures that the eMagiz Cloud is only affected when a user want to affect it

Below we have categorized each action to see whether they have a direct effect on the eMagiz Cloud or an Indirect effect. This is to give context per action what is the consequence of your action.

| <p align="center">**Direct Effect**</p>| <p align="center">**Indirect Effect**</p>|
| ------ | ------ |
| Restart Runtime (Not JMS) | Add Route |
| Restart Runtime (JMS) | Update Route |
| Reset Runtime (Not JMS) | Delete Route |
| Reset Runtime (JMS) | Add Certificate |
| Restart Runtime (Not JMS) | Update Certificate |
| Restart Connector Machine | Delete Certificate |
| Restart Core Machine | Add runtime to connector machine |
| Stop Connector Machine | Add runtime to core machine |
| Stop Core Machine | Remove runtime from connector machine |
| Start Connector Machine | Remove runtime from core machine |
| Start Core Machine | Update memory settings runtime (not JMS) |
| Wake up Cloud Slot | Update memory settings runtime (JMS) |
| Put Cloud Slot to sleep | Change Cloud Template |
| Clean Store | |
| Upgrade Cloud Slot* | |

*Note that the upgrade of the cloud slot can be planned for a later moment in time.

So in short when you execute one (or more) actions on Deploy Architecture that have an indirect effect you need to press Apply to Environment to actualize the changes within the eMagiz Cloud. Note that each action, whether it is direct or indirect, will cause a reaction and subsequent change within the eMagiz Cloud. So be cautious about changing things too many times over.

##### Practice

## 4. Assignment

There is no assignment for this microlearning.

## 5. Key takeaways

- By restarting the runtime, you restart all flows (including infra) of the runtime you have selected
    - Flows return in original state

##### Solution

## 6. Suggested Additional Readings

There are no suggested additional readings on this topic

## 7. Silent demonstration video

There is no demonstration video of this functionality. 

</div>
</main>
</div>
</div>