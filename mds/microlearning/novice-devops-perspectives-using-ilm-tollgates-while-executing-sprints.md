<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/novice-devops-perspectives-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Using ILM tollgates while executing sprints

In this microlearning, we will focus on the use of tollgates while using the eMagiz platform to develop functionality for the customer (with the help of sprints). By using these tollgates you can increase the quality of work.

Should you have any questions, please contact academy@emagiz.com.

- Last update: May 9th, 2021
- Required reading time: 9 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around using ILM tollgates.
With tollgates, we mean: A list of items that can be inserted into Definition of Done lists that are used

Key aspects are
- Organized around the Integration LifeCycle of eMagiz
- A good business ready designs for every integration
- Ensure all steps required are taken
- Can help with peer reviews
- Increases quality of the work that is delivered

##### Theory

## 3. Using ILM tollgates while executing sprints

In this microlearning, we will focus on the use of tollgates while using the eMagiz platform to develop functionality for the customer (with the help of sprints). By using these tollgates you can increase the quality of work.

Key aspects are
- Organized around the Integration LifeCycle of eMagiz
- A good business ready designs for every integration
- Ensure all steps required are taken
- Can help with peer reviews
- Increases quality of the work that is delivered

In the remainder of this section, we will zoom in on these various tollgates. Before we do so first introduce the concept a little bit more. 

Tollgates in this context are the list of items that can be inserted into Definition of Done lists that are used. These tollgates are organized around the Integration LifeCycle of eMagiz (Capture, Design, Create, Deploy and Manage), further referred to as the ILM. The ILM has the intention to take each new or changed integration through a guided process to ensure all steps required are taken. For most of these process steps, certain elements can be verified before continuing which can help peer reviews and prepare deployments. Further, these items will help you to make good business-ready designs for every integration. 

Depending on the structure used in the user story writing for DevOps teams, these DoD items can be set properly at the right location. For instance, the Capture & Design ILM phases are often put into a single User Story so that tollgates T1 and/or T2 can be connected to this User Story as DoD items. Situations are different every time, the intention is to provide some inspiration to the DevOps team with daily eMagiz activities.

The tollgates are described below in terms of a list of suggestions per tollgate. For more information on the Integration Life Cycle, please check out the documentation menu to find out more.

<p align="center"><img src="../../img/microlearning/novice-devops-perspectives-using-ilm-tollgates-while-executing-sprints--tollgates-in-combination-with-ilm-phases.png"></p>

### 3.1 Tollgate T1 – Business Ready

The objective of this tollgate is to validate the business value to add new integrations before starting the actual change in eMagiz. 

- Background and necessity of the new integration
- Sense of urgency and deadlines
- What are the business processes involved
- What is the criticality of the business process and what indicators are used to measure this
- What type of information is exchanged?
- What are the assumptions, preconditions, and dependencies from a business point of view
- Are there legal implications or requirements
- What is the impact on architectural principals
- Is there formal approval from key stakeholders to implement this integration?

### 3.2 Tollgate T2 – Discovery Done

The objective of this tollgate is to ensure all aspects of the integration are properly validated and agreed upon with the business before creating the actual integration.

- Clarity on scope, effort, risks, and impact (story points)
- Capture 100% completed
- Design 100% completed (CDM, Message definitions, and Design Architecture)
- Definitions from both system stable and final
- High-level design available
- Impact on eMagiz Cloud resource known
- Impact on timelines with associated teams and involved application agreed
- Summary presentation available with a summary of Discovery and approved by key stakeholders

### 3.3 Tollgate T3 – Delivery Ready (to start)

The objective of this tollgate is to validate if the create phase can start - are all information elements available?

- Connectivity test on environments from source and target system completed
- Handover from eMagiz Architect to eMagiz DevOps team completed
- Definitions from both system stable and final
- example messages available and representative
- Test scenario's created by business ready and available

## 3.4 Tollgate T4 – Delivery Done

The objective of this tollgate is to validate if the Create phase has been properly completed - focus on review and peer review.

- Create completed 
- All flows are part of a Release and are running stable without errors on Test
- Unit tests are available and stable
- Peer review completed
- End to end test with business completed
- Test report presented and agreed with business stakeholders


## 3.5 Tollgate T5 – Ketentest Ready (to start)

The objective of this tollgate is to ensure the business can test the new or changed integration in the Acceptance environment.

- Unit test completed on Acceptance
- Test scenarios are accepted by the business
- Criteria for a successful end to end test known
- Acceptance environments of involved systems are representative for the integration to test
- Dates are agreed jointly to run the test
- eMagiz specifics
    - All flows are released on Acceptance
    - Connectivity check done on Acceptance
    - Properties are properly configured on Acceptance
    

## 3.6 Tollgate T6 – Go-live Ready

The objective of this tollgate is to prepare the Go-live of the Release to production

- End to end test completed
- Go live plan ready and reviewed
- Go live date agreed with the business
- Rollback scenario's ready
- Risk assessment completed and actions set out
- eMagiz specifics
    - All flows are inside a proper release
    - Connectivity check done on Production
    - Properties are properly configured on Production
    - Deploy Architecture current

## 3.7 Tollgate T7 – Go-live Done

The objective of this tollgate is to validate the production environment if the Release is running on Production.

- No warnings or errors that can't be explained or for which no plan is in place
- Alerting updated
- Transfer to Support completed in case of a Model SLA
- All systems are live.

##### Practice

## 4. Assignment

Determine for the project(s) you are currently working on to which extent you are using the above tollgates and identify possible improvement points to increase the quality of work.

## 5. Key takeaways

- Key aspects are
    - Organized around the Integration LifeCycle of eMagiz
    - A good business ready designs for every integration
    - Ensure all steps required are taken
    - Can help with peer reviews
    - Increases quality of the work that is delivered

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read up on Scrum.

## 7. Silent demonstration video

As this is a theoretical microlearning no video is made.

</div>
</main>
</div>
</div>