<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/fundamental/index_academy_fundamental_all" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>
<div class="doc">
 
##### Intro

# eMagiz Stateful
 
In this fundamental, we'll take a look at the capability of eMagiz around storing a state of a data packet of message send across the platform.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: March 7th, 2022
- Required reading time: 10 minutes

## 1. Prerequisites

- Take a closer look at the Fundamentals for Messaging, API Gateway and Event Streaming


## 2. Key concepts
All concepts are discussed in the section below.

##### Theory
  
## 3. Introducing Stateful

Within eMagiz there is a capability to store pieces of data of a specific object that is transit between systems. The basis idea of messages that are processed by eMagiz is that all of these are in transit. However, in certain cases it is very helpful to preserve a state of an object. That state can help to influence the next data packets that are passing through or trigger a certain action for another system.

An example might be a situation where a sensor is submitting temperature data every 5 seconds on a data stream towards eMagiz. The interesting state of the machine where the sensor is attached to is the average temperature in the last hour. In this case the temperature that is send to the eMagiz should be used to update the state of the machine, and more specifically the average temperature. One needs a data stream from the sensor, a way to aggregate & average out all messages from the last hour, and a way to store the state. Once the temperature reaches a certain threshold, the data is submitted to a next system to raise an alert for a user.

Another example might be a data stream that registers a click on a specific webpage. That data stream is connected to eMagiz, whereby the state of that specific webpage is updated with the number of clicks. Once the number of clicks in the last 30 minutes reaches for instance more than 50, a specific action might be triggered. If that page contains a product, the action might be to display the number of web users active on that product in order to influence the sales of that product. One needs a data stream, a way to count the number of click, and a way to store the state of that webpage.

The example are purely illustrative to understand the concept. 

#### 3.1 State Store

The state store refers to the storage location of the states of the specific objects in the environment. That storage location is part of the eMagiz platform, and embedded in the eMagiz runtime for now. The user needs to define what objects and the attributes of that object are to be stored. Several different objects and states of the objects can be be defined & stored. A state store can be shared across multiple processes that are allowed to update the state of an object.

#### 3.2 State Operations

Once the state store is defined, one needs different operations in order to update the state effectively. 
- Retrieve - get the values of an object and the attributes
- Aggregate - Increment a attribute in a state store to +1
- Enrich - add new attribute of an object in the state store based on joining several streams
- Transform - filter data or translate formats
- Time-window - to aggregate data over time

#### 3.3 State Action & networks

Once the state store has values stored, certain triggers can be defined to cause action. For instance, when the temperature is higher than 20 in the example above. These actions can be defined/modeled by the eMagiz user inside flows, whereby the evaluation of state would send a data point to the system that manages the action. For instance, the support team that manages the server park and needs to verify of the airconditioning of the server room is working properly (case high temperature).

One can imagine that a certain action would be to update the state of another object. Or that there are several other data streams are update several states. In that way, you can imagine a complete network of data that work intertwined for you to detect rolling reality of data that can be used for data analysis and real-time decision-making.

#### 3.4 Speed and throughput

Many organizations hold lots of data which can be leveraged for such use cases, and often include IoT like data. Therefore, the data is usually put on event streams that are geared towards speed and throughput. In eMagiz you will find these data points usually in topics that are processed by Event Processor flows.

#### 3.5 Pattern specifics

At first hand it looks as if these concepts would only apply to Event Streaming. But capturing & storing a state of an object would also be handy in other patterns such as Messaging. For instance, when the order of the messages being send matters, or when there is dependency between messages that is needed to determine when a message needs to be send in time.


#### 3.6 eMagiz specifics

The state store is implemented inside the eMagiz runtime using the H2 database for now. For time related operations another technology is used (Esper), and the functionality is only available on Docker based runtimes (to be release end Q2 2022). You wil find the specific Stateful components inside the Flow Designer as we use in eMagiz to model the flow. Aligned with the general concept of low-code developnment in eMagiz. For State store models, the current data modeling capabilities will be used. 


##### Practice

## 4. Key takeaways

- Stateful refers to the concept of storing a state of an object
- Storing a state is different compared to data in transit which is often refered as stateless data (eMagiz doesn't store or update the data when sending across)
- Stateful can be applied across all patterns in eMagiz and is embedded into the platform in such a way that it provided the same user experience


##### Solution

## 5. Suggested Additional Readings

N/A

## 6. Silent demonstration video

N/A

</div>
</main>
</div>
</div>