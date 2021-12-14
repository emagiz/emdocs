<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-monitoring-eventstreaming-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Monitoring Topic size

Topics are a vital part of any Event Streaming solution. Each topic will have an assigned size and understanding the size across time and context is important to ensure the right sizing is chosen for these topics.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: November 1st, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- Complete relevant Event Streaming microlearnings from Crash course to Intermediate

## 2. Key concepts
Based on the lines you drew in Capture eMagiz automatically generates a topic. In other words, for each line you drew in Capture eMagiz will create an accompanying topic. As a reminder, a topic is a category/feed name to which event records are stored and published. All Kafka records are organized into topics. Producer applications write data to topics and consumer applications read from topics. Records published to the cluster stay in the cluster until a configurable retention period has passed by.

##### Theory
  
## 3. How to monitor topic sizing

In the Design phase you can set the required size of a topic. That size serves as the retention size, which effectively means that once the topic size reaches that threshold the retention policy will ensure that the oldest messages on the topic are deleted. 

It's relevant to understand whether the design size is actually sufficient to serve the business process for which the topic was create for. In case there is insufficient topic size, it could mean that some messages are deleted too early and are not considered for the business process. Futhermore, there are limits in the use of topic size in the eMagiz Cloud. An oversized topic could mean that other topics will not have sufficient storage available for instance. Or some test topics are configured with too much storage which negatively influences the overall size. 

To make these right decisions and configuration for topic sizing, you can review the actual size of each topic in the Manage phase. Navigate to the Manage phase and select the Monitoring section. In the left hand menu you will the option Topic Statistics. The column partition size displays the total actual size of the topic across the partitions of that topic. In case the topic has more partitions, the value of partition size is the sum of these topics. 

<p align="center"><img src="../../img/microlearning/advanced-monitoring-eventstreaming-monitor-topicsize-1.png"></p>

- Please note that the column retention size is the size per partition - in case you have 5 partitions that value needs to be multiplied by 5 to understand the true total retention size on a topic level
- There is a fixed value (called segment size) in the eMagiz Cluster that is used as a threshold before the retention policy kicks in and starts to delete data. This value is set to 220 Mb, which means that in case the retention size of the topic is less than 220 Mb the last 220 MB are always available
- In the Design phase, the display of the Assigned topic size takes into account this segment size for calculation purposes

##### Practice

## 4. Assignment

Take a moment to review your Event Streaming solution and find the Manage - Montoring section to see the topic statistics. Review if you can reproduce the numbers above.

## 5. Key takeaways

- Topic statistics are available in the Manage - Monitoring section and can be used to see the actual size of the topic
- Decisions around sizing of topics can be made using these monitoring data points to determine the optimal configuration of topics across environments

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information, please read the release notes provided by eMagiz.

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video that accompanies this microlearning.

</div>
</main>
</div>
</div>