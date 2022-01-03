<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-keyconcepts-eventstreaming-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Impact of changing topic retention 

In this microlearning, we'll take a look at the impact of changing retention polices for topics across time. A retention policy defines at what thresholds data is deletedf from a topic.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: December  2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- Complete relevant Event Streaming microlearnings from Crash course to Intermediate

## 2. Key concepts
Retention configuration in Event Streaming helps to delete data from a topic once that data (messages) reaches one of the retention thresholds. The main retention parameters that can be influenced in Event Streaming topis are:

1. Retention bytes - once the topic reaches this size the oldest messages will be deleted from the topic (FIFO approach)
2. Retention hours - once a message on a topic is older than these retention bytes, this message will be deleted

The cleanup policy is set to <delete> which effectively means the message is deleted. The cleanup policy <compact> is not used in eMagiz.

##### Theory
  
## 3. Considerations for topic retention policy

### 3.1 When does the retention kick in?
Retention will only start when the topic size is larger than 220Mb for topics that are less than 200Mb. The socalled segment size is automatically calculated and is considered for topics larger than 220Mb. It may occur that data is not yet deleted at the moment the size of the topic is larger than the retention size configured.

### 3.2 Does the size in Design Architecture consider the segment size?
The total size in eMagiz that is displayed in the Design phase - Architecture takes into account the complex calculations around segment sizing, cleanup policies etc. So your sizing can never exceeed that value on our Event Streaming cluster. eMagiz uses this value to determine the required licensing. 

### 3.3 Actual retention vs. budget retention
Despite the fact that you set a retention hours setting, it may occur that the amount of messages is so large that the retention bytes kicks in earlier than the retention hours. This could cause an effect that the oldest messages is younger than your retention hour setting. In specific scenario's this can be an issues


### 3.4 Managing retention across TAP
You are able to set the retention bytes and hours per Test, Acceptance and Production. You can play with this configuration values by setting a smaller value for Test compared to Production. So that each topic is optimized for the environment at hand. One advice can be to keep Acceptance and Production similar in terms of configuration for retention - test can be set to a lower value. 

During development of a new business process that involves the use of topics, only test can be given sufficient retention values. In this case, Acceptance and Production topics can be disabled so that the total licensed size is not exceeded.

### 3.5 Duplication of data
- At this moment the standard setting for the number of partitions is 1. In case you change this value to 10, then you will have a reserved data storage of 10 times the retention bytes. The grand effect might be that the when adding all topics together including the segment size could increase the total size substantially.

- When design solutions in eMagiz using Event Streaming, then make sure to make the right decision on the storage of intermediate results. You could store a intermediate result of a process step in a next topic that then in turn takes the next step in the business process. In this case, it might be that the use of too many topics for the same business process causes an exponential increase of data storage. Try to make a sound decision in this by combining steps or alternative.


##### Practice

## 4. Assignment

Take a moment to review your Event Streaming solution and find the Design Architecture section. Review the additional readings to ensure the management of topics and their retention settings are clearly understood.

## 5. Key takeaways

- There are 2 ways to influence the retention of a topic - hours & bytes
- Deletion of data in a topic based on retention policy is somewhat complex - be sure to understand the size of a topic before deletion kicks in
- Be careful in configuring topics so that data is not duplicated unnecessary and each environment has the right retention policy

##### Solution

## 6. Suggested Additional Readings

1. Understanding retention policy in eMagiz: https://emagiz.github.io/docs/microlearning/intermediate-key-concepts-emagiz-event-streaming-retention-policy
2. Understanding topic configured size across environments: https://emagiz.github.io/docs/microlearning/intermediate-solution-architecture-topic-storage
3. Key concepts of Event Streaming: https://emagiz.github.io/docs/fundamental/fundamental-event-streaming-introduction

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video that accompanies this microlearning.

</div>
</main>
</div>
</div>