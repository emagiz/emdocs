<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/rca-knowledgebase/index_academy_rca-knowledgebase_all" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# RCA - Data loss during a production change

In this document, we will use the information from the actual root cause analysis to make a generic view that can be used if you run into the same or a similar problem in the future. Finally, the document will describe the situation, the problem, the analysis, and the result.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: March 8th, 2022
- Required reading time: 4 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform


## 2. Key concepts
- When executing a change in production, always consider the impact
- Temporary data is not kept when resetting a runtime in the cloud

##### Theory

## 3. RCA - Data loss during a production change

In this document, we will use the information from the actual root cause analysis to make a generic view that can be used if you run into the same or a similar problem in the future. Finally, the document will describe the situation, the problem, the analysis, and the result.

Below we have written down various phases to help you determine whether this document can help you identify and resolve your problems.

### 3.1 Situation
On a specific working day, unplanned maintenance occurred in a production environment to solve a memory issue on one of the runtimes. The unexpected maintenance resulted in a user pressing the Apply to Environment button in Deploy -> Architecture in eMagiz. As a result, the complete machine was stopped, recreated, and started again.

### 3.2 Problem
As a result of these actions, reports came in that data was lost between retrieval from an SFTP and delivery to a Mendix application.

### 3.3 Analysis

#### 3.3.1 Logging in AWS
To analyze the problem, we dove into the eMagiz logging in AWS. During the restart, we see among other errors the following errors. The first indicates that the synchronization with the SFTP got interrupted. The second implies that the delivery of the order response failed because the thread got interrupted.

Furthermore, it is noticeable that this specific runtime is restarted several times within two minutes. For example, at 12:16:20, we see logging appearing that connection attempts are made between eMagiz and the SFTP. This ultimately results in messages being picked up by eMagiz at 12:17:05 and onwards.

#### 3.3.2 Analysis of entry

After inspecting the logging surrounding the incident, we analyzed the flow itself. Here we see that the SFTP is polled every 15 seconds, and per poll, a maximum of 100 messages can be synchronized. This means that the call for which we see an error in the log that the connection broke down could hold up to 100 messages that are not completely processed.
Furthermore, we see that no filter is used when retrieving files from the SFTP. This means that each file is only accepted once. This is a possible risk when data is retrieved but not correctly deleted. This could lead to a mismatch between what is on the SFTP and what is processed by eMagiz. 

Upon further investigation, we see that the H2 database that stores the temporary data between retrieval and placing it on the queue was recreated during the Apply to Environment action. This means that everything that was in the database at that moment is gone. So we can conclude that the inbound folder was recycled as part of the update of the single lane connector.

### 3.4 Result

The analysis concluded that the Apply to environment action to solve one problem created another problem within the environment. To safeguard against these actions, take the following steps:

- Change the location of the local directory. The data needs to be stored in the data folder of eMagiz or on EFS. Verify with the help of support that the folder is created in the correct location 
- Assess the impact of upgrades and shut down business-critical processes before performing an upgrade

##### Practice

## 4. Key takeaways

- When executing a change in production, always consider the impact
- Temporary data is not kept when resetting a runtime in the cloud

</div>
</main>
</div>
</div>