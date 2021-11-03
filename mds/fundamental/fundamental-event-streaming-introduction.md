<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/fundamental/index_academy_fundamental_event-streaming" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>
<div class="doc">
 
##### Intro

# eMagiz Event Streaming - Introduction
 
In this microlearning, we will introduce the most important concepts of Event Streaming.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: November 3rd 2021
- Required reading time: 10 minutes

## 1. Prerequisites
- Completed the crashcourses of eMagiz


## 2. Key concepts
All concepts are discussed in the section below.

##### Theory
  
## 3. Introducing Event Streaming

Event Streaming is the concept whereby systems can produce data and consume data from a single location. In the integration world this integration pattern is referred to as Publish-Subscribe (or PubSub). The single location is called a topic, the Pulisher is often called a Producer and a Subscriber a Consumer. The key is that a topic may contain multiple Publishers of the same data, and may contain more Subcribers of the same data. Consumers are subscribed to a topic and will receive a notification that triggers a read action. Core focus of Event Streaming is high-volume and high-speed.

<p align="center"><img src="../../img/howto/fundamental-event-streaming-introduction-1.png"></p>

### 3.1 Topics
Topics are the things where the message or data packets is stored. It is not a conventional database, and uses a logbased approach to store data. Each new data packet is put on top of the stack and an offset indicator is added which helps consumers to understand which message is read or which ones not. The data on the topic can be spread in multiple partions which are the smallest technical unit where a data packet is written into. Having multiple partions makes it possible to read /write data at ultra-high speed by Consumers/Producers.

Data in topics are focus on storing small events which are no bigger than 1 Mb per data packet/message.

<p align="center"><img src="../../img/howto/fundamental-event-streaming-introduction-2.png"></p>

### 3.2 Retention

Retention is an important concept as that allow to clear messages from the topic in an organized manner. The key is that data should be kept on the topic fo a limited amount of time or limited amount of size.

#### 3.2.1 Retention Hours

Retention Hours is the number of hours data can reside on the topic before a FiFo principle of removing the first entry in the log kicks in. The moment data is still on the topic beyond this threshold it will automatically start deleting the data. The default setting eMagiz provides you is 168 hours (7 days). 

#### 3.2.2 Retention Bytes

Retention Bytes is the number of bytes available per partition on that topic before a FiFo principle of removing the first entry in the log kicks in. The moment your topic holds more bytes as compared to the retention byte setting it will automatically start deleting the data. The default setting eMagiz provides you is roughly 500 MB. 

### 3.3 Replication
The default replication mechnanism is that the data will be spread across 3 different nodes so that no data is lost, high availability is ensured and high performance is guaranteed. Event Streaming distributes the partitions of a particular topic across multiple brokers. By doing so, we’ll get the following benefits.

- If we are to put all partitions of a topic in a single broker, the scalability of that topic will be constrained by the broker’s IO throughput. A topic will never get bigger than the biggest machine in the cluster. By spreading partitions across multiple brokers, a single topic can be scaled horizontally to provide performance far beyond a single broker’s ability.
- A single topic can be consumed by multiple consumers in parallel. Serving all partitions from a single broker limits the number of consumers it can support. Partitions on multiple brokers enable more consumers.
- Multiple instances of the same consumer can connect to partitions on different brokers, allowing very high message processing throughput. Each consumer instance will be served by one partition, ensuring that each record has a clear processing owner.

### 3.4 Reading data from a topic
Consumers can read data from a topic at their own pace and availability. Event Streaming doesn't push messages - consumers need to come and get the data. The offset of a message works as a consumer side cursor at this point. The consumer keeps track of which messages it has already consumed by keeping track of the offset of messages. After reading a message, the consumer advances its cursor to the next offset in the partition and continues. Advancing and remembering the last read offset within a partition is the responsibility of the consumer. Event Streaming has nothing to do with it.

<p align="center"><img src="../../img/howto/fundamental-event-streaming-introduction-3.png"></p>

### 3.4 The Event Streaming Broker

The Event Streaming Broker holds the technical infrastructure to manage all these topics, Producers/Consumers associated, etc. The Kafka framework is used inside the eMagiz Event Streaming to enable this technology piece. The entire Event Streaming Broker is part of the eMagiz platform and fully managed from the platform.

### 3.5 Event Processing
eMagiz reuses the transformation capability to allow transformation of messages. In this pattern, messages are transformed in special type flows called Event processors. The Event processor will use a topic in and topic out which means that data is transported from 1 topic to another. On each topic you can define an event data model. 

<p align="center"><img src="../../img/howto/fundamental-event-streaming-introduction-4.png"></p>

### 3.5 Event Data Model
For each of the topics in the eMagiz platform, you can define a message definition. These message definitions are used for Event Processors but also for the Event Catalog where external users can browse the topics.

### 3.6 Event Catalog
The event catalog allows external users to browse the content for each of the topics where that user has access to. These special type users need to be registered in the eMagiz platform, and upon accessing the eMagiz Portal these users will have a single access to the list of topics and the relevant meta data of that topic.

<p align="center"><img src="../../img/howto/fundamental-event-streaming-introduction-5.png"></p>

### 3.7 Kafka Connector for Mendix
eMagiz has developed a connector for Mendix that allows the production and consumption of messages from/to the Event broker. Please refer to this page to learn more about this: https://marketplace.mendix.com/link/component/118323


##### Practice

## 4. Assignment

There is no specific assigmment here. Please review the Use case for Event streaming more closely to learn more about the configuration in eMagiz.

## 5. Key takeaways

- Event Streaming holds a few important concepts to know. Please ensure to read the above carefully before moving to the next part of this Fundamental.

##### Solution

## 6. Suggested Additional Readings

- https://www.emagiz.com/event-streaming/


## 7. Silent demonstration video

There is no video available as this is more a theoretical microlearning.

</div>
</main>
</div>
</div>