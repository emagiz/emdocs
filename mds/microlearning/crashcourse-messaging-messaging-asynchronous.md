<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/crashcourse-messaging-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Messaging Asynchronous

In this microlearning, we will explain the basics of the asynchronous messaging pattern.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: February 25th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around the asynchronous messaging pattern in eMagiz.
By asynchronous, we mean: The process that processes data without returning to the sending system with an update on whether the data was processed successfully.

Key characteristics of asynchronous messaging are:

- Non-blocking. The sender initiates the process and can continue with the following message
- Systems can therefore be loosely connected
- Messages can temporarily be kept in the queue if an end system to which the messages need to be delivered is scheduled to go offline
- Supports one-to-many distribution of messages over the integration landscape

##### Theory

## 3. Messaging Asynchronous

Asynchronous messaging is the pre-dominant option when you implement a messaging integration via eMagiz. 
Key characteristics of asynchronous messaging are:

- Non-blocking. The sender initiates the process and can continue with the next message
- Systems can therefore be loosely connected
- Messages can temporarily be kept in the queue if an end system to which the messages need to be delivered is scheduled to go offline
- Supports one-to-many distribution of messages over the integration landscape

With this method, the sending party supplies the data to eMagiz (via push or pull). eMagiz, in turn, places the data on a queue (in most cases an onramp queue).

This logic means there is no need for the external system to wait for a reply to see what the other system thinks of the message. 
Furthermore, the system can supply the data somewhere and forget about it. eMagiz will ensure to deliver the information to all systems that want to receive the data.

Because of this loose coupling between systems via the asynchronous five-layer model in eMagiz, you can add supplying and receiving systems quickly and replace them if necessary.

On top of that, it gives you the option to keep data in a queue temporarily. This functionality is, for example, convenient if there is scheduled maintenance in one of the receiving systems. 
The sending system can continue to send data to eMagiz, and eMagiz will keep it in the queue until the scheduled maintenance is finished.

##### Practice

## 4. Assignment

Analyze an asynchronous messaging flow from entry to exit and determine which queues are used in the process. 
This assignment can be completed with the help of your (Academy) project you have created/used in the previous assignment.

## 5. Key takeaways

- Asynchronous messaging is the pre-dominant option when you implement a messaging integration via eMagiz. 
- Key characteristics of asynchronous messaging are:
    - Non-blocking. The sender initiates the process and can continue with the next message
    - Systems can therefore be loosely connected
    - Messages can temporarily be kept in the queue if an end system to which the messages need to be delivered is scheduled to go offline

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information, please read the help text provided by eMagiz.

## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned.

<iframe width="1280" height="720" src="../../vid/microlearning/crashcourse-messaging-messaging-asynchronous.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
</main>
</div>
</div>