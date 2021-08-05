<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-key-concepts-emagiz-messaging-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Entry, not a queue
 
In this microlearning, we will explore what the function of the entry is within the message engine. Furthermore, we will explain why there is no entry queue.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: August 5th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Intermediate knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on the concept of entry, not a queue.

- The key aspects are:
    - Entry is the starting point of the integration process in messaging
    - Queues are an internal resource of eMagiz
    - Outside parties are not allowed to write on eMagiz queues directly
    - eMagiz facilitates various connectivity methods (i.e., REST, SOAP, Database, File)

##### Theory
  
## 3. Entry, not a queue

In this microlearning, we will explore what the function of the entry is within the message engine. Furthermore, we will explain why there is no entry queue.

- The key aspects are:
    - Entry is the starting point of the integration process in messaging
    - Queues are an internal resource of eMagiz
    - Outside parties are not allowed to write on eMagiz queues directly
    - eMagiz facilitates various connectivity methods (i.e., REST, SOAP, Database, File)

As you learned from the introductory course on messaging, we use a five-layer approach to handle data within the messaging engine. The first layer the data encounters is the entry. The goal of the entry is twofold. One is to establish a connection with an external system. The other is to place data on a queue. There are two ways to establish connectivity. The first method is via a pull mechanism. This pull mechanism means that eMagiz will initiate the communication to retrieve data. The second method is a push mechanism. This push mechanism means that eMagiz will patiently wait till the external system offers data to eMagiz. The push mechanism will typically be realized with the help of a hosted web service (REST or SOAP) within your eMagiz solution.

Since the goal of the entry is connectivity between the external system and eMagiz, you could argue that it would be easy to let them place the data on the queue. However, things are not that easy. There are several reasons why this is not a best practice:

- This would mean that the external system directly needs to connect to the infra layer (the JMS) and will have the option to read and write on other queues as well
- This would mean that the external system can only push data to eMagiz (so no polling of data)
- This would mean that the external system can directly place data on a queue
- This would create a tightly coupled dependency between the external system and eMagiz

The above arguments concluded that the connectivity between eMagiz and the external system and the internal queue mechanism of eMagiz should be considered two separate things. This conclusion did raise a question on how eMagiz can guarantee message delivery. The messaging engine uses queues to ensure message delivery. But what if the first queue (the onramp queue) cannot be reached? What happens then.

The H2 database is introduced to safeguard against any problems within the entry. This component is generated in every entry in eMagiz. This H2 database will temporarily store data and act as a bridge between the entry and the onramp queue. This way, eMagiz can guarantee message delivery. If you want to learn more about the function of the H2 database, please check out this [microlearning](intermediate-solution-architecture-function-of-h2-database.md).

To summarize:
- Entry is the starting point of the integration process in messaging
- Queues are an internal resource of eMagiz
- Outside parties are not allowed to write on eMagiz queues directly
- eMagiz facilitates various connectivity methods (i.e., REST, SOAP, Database, File)

##### Practice

## 4. Assignment

No assignment accompanies this microlearning.

## 5. Key takeaways

- The key aspects are:
    - Entry is the starting point of the integration process in messaging
    - Queues are an internal resource of eMagiz
    - Outside parties are not allowed to write on eMagiz queues directly
    - eMagiz facilitates various connectivity methods (i.e., REST, SOAP, Database, File)

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic, please boost your knowledge with the help of the internet.

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video for this.

</div>
</main>
</div>
</div>