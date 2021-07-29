<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-solution-architecture-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# H2 Database, Function
 
When you utilize the messaging platform you are bound to see this component automatically appear in all your entries when you create those entries for the first time. However, we see that there is quite some confusion on what the function of this component is in the entry. In this microlearning, we will try our best to explain that function to you. In another microlearning, further down the road, we will discuss other applications of the H2 database.

Should you have any questions, please contact academy@emagiz.com.

- Last update: July 29th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on the function of the H2 Database.

With H2 Database we mean: A database structured that can be created and used with the help of eMagiz components

The focal point of this microlearning will be to figure out why the H2 database is part of any auto-generated entry.

- The key aspects are:
    - H2 Database temporarily stores data
    - Acts as a bridge between the entry (where data arrives or is retrieved) and the first queue (the onramp)
    - Holds data in case the queue (the onramp) cannot be reached
    - Smooths out the amount of data that is transported from the connector to the container runtime as it periodically checks for new data

##### Theory
  
## 3. H2 Database, Function

When you utilize the messaging platform you are bound to see this component automatically appear in all your entries when you create those entries for the first time. However, we see that there is quite some confusion on what the function of this component is in the entry. In this microlearning, we will try our best to explain that function to you. In another microlearning, further down the road, we will discuss other applications of the H2 database.

The focal point of this microlearning will be to figure out why the H2 database is part of any auto-generated entry.

- The key aspects are:
    - H2 Database temporarily stores data
    - Acts as a bridge between the entry (where data arrives or is retrieved) and the first queue (the onramp)
    - Holds data in case the queue (the onramp) cannot be reached
    - Smooths out the amount of data that is transported from the connector to the container runtime as it periodically checks for new data

As you probably noticed by now is that every time you create a new entry in eMagiz some components are automatically generated for you.

<p align="center"><img src="../../img/microlearning/intermediate-solution-architecture-topic-storage--auto-generation-entry.png"></p>

A subset of these components creates the desired H2 database including structure to receive and process messages. Those components are highlighted in the picture below.

<p align="center"><img src="../../img/microlearning/intermediate-solution-architecture-topic-storage--auto-generation-entry-h2-components.png"></p>

The support objects ensure that the H2 database is created and that the data in it is encrypted. Furthermore, they make sure that the database is stored in the proper location and has the correct structure. All of this is nothing you as a user should worry about. Those support objects are created with the best possible settings.

Another part of the flow is the grey circle that will become part of your main flow. This component is called a message bridge. With the help of the message bridge, you can link up certain channels to throttle messages and make sure that the endpoint (in this case the queue) does not have to do the polling on the database to check for new messages. The default setting for this component is that every 500 milliseconds 10 messages are picked up. Based on desired throughput and volume you could tweak those settings to best suit your needs. Do be aware that you should not randomly start tweaking settings.

Furthermore, this message bridge is linked to a support object (transaction manager). This configuration allows the poller action to be part of the transaction and therefore gives the ability to perform a rollback in case of error. This is crucial when you want to guarantee message delivery. If you would not have something like this and for whatever reason, the connection between the entry and the queue (the onramp) is gone messages will be lost.

<p align="center"><img src="../../img/microlearning/intermediate-solution-architecture-topic-storage--auto-generation-entry-h2-transaction-manager.png"></p>

So what eMagiz gives you is a standardized database structure that temporarily stores messages (in case of connection issues). This is to ensure guaranteed delivery of the incoming message on the first queue in eMagiz (the onramp). As a bonus, the component helps you to smooth out the messages that are placed on the queue for further processing. With the help of this component, you prevent that when an external system offers 1000 messages within seconds all 1000 will end up on the queue at the same time. If that would happen you could run the risk of overloading your queue leading to larger issues (potentially even an 'out of memory' of the container).

Hopefully, this microlearning will give you some context on why the H2 database is automatically generated by eMagiz in every entry and plays a crucial role in holding up to the promise of guaranteed delivery of messages within the platform.

##### Practice

## 4. Assignment

Reflect on the choices made within various projects and see if you would, with what you know now, change the specific implementation.

## 5. Key takeaways

- The key aspects are:
    - H2 Database temporarily stores data
    - Acts as a bridge between the entry (where data arrives or is retrieved) and the first queue (the onramp)
    - Holds data in case the queue (the onramp) cannot be reached
    - Smooths out the amount of data that is transported from the connector to the container runtime as it periodically checks for new data

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help texts provided by eMagiz

## 7. Silent demonstration video

As this is a more theoretical microlearning we have no video for this

</div>
</main>
</div>
</div>