<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-key-concepts-emagiz-event-streaming-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Retention Policy
 
In this microlearning, we will dive a little bit deeper into the concept of the retention policy concerning Event Streaming. Retention policy determines when a message needs to be cleaned up and, if so, what will happen to the message.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: August 4th, 2021
- Required reading time: 4 minutes

## 1. Prerequisites
- Intermediate knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on the retention policy for Event Streaming.

- The key aspects are:
    - Retention Hours
    - Retention Bytes
    - Cleanup Policy
    - These three items determine the retention policy

##### Theory
  
## 3. Event Streaming

In this microlearning, we will dive a little bit deeper into the concept of the retention policy concerning Event Streaming. Retention policy determines when a message needs to be cleaned up and, if so, what will happen to the message.

- The key aspects are:
    - Retention Hours
    - Retention Bytes
    - Cleanup Policy
    - These three items determine the retention policy

As we learned in the introductory [microlearning](crashcourse-eventstreaming-event-streaming-introduction.md), the topic holds a log with a sequence of messages. Based on several criteria, the broker decides when to remove messages from the back of the log to ensure that the topic stays within specific parameters. These parameters are the retention hours and the retention bytes. If you want to learn more about them specifically, please check out this [microlearning](crashcourse-eventstreaming-topic-and-topic-properties.md).

These parameters combined with the cleanup policy determine what happens with a message after it is expired. There are two options available:
delete
compact
The delete option is the default that eMagiz uses and advises. This option will, as the name suggests, delete all messages that are expired. There is an alternative approach called compact. This functionality will enable log compaction on the topic.

The three aspects combine to make up the retention policy. Defining the correct values for both the retention hours and the retention bytes is a science as a form of art. As you only have limited storage capacity available, the challenge becomes how much retention you reserve per topic. The more you assign, the less free storage capacity remains for other topics. As a consequence, you need to strive to optimize your retention policy per topic continually.

##### Practice

## 4. Assignment

Check out if you have a project in which the Event Streaming pattern is used. If so, check out the retention policy for several topics.

## 5. Key takeaways

- The key aspects are:
    - Retention Hours
    - Retention Bytes
    - Cleanup Policy
    - These three items determine the retention policy

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic, please read the help text eMagiz provides you.

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video for this.

</div>
</main>
</div>
</div>