<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-keyconcepts-apigateway-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Considerations for API Gateway or Messaging

In this microlearning we'll take a moment to discuss several considerations for making the right choice between the two patterns

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: December 2021
- Required reading time: 10 minutes


## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- Completed the relevant microlearnings Key Concepts API Gateway (level crash course to intermediate)
- Completed the relevant microlearnings Key Concepts Messaging (level crash course to intermediate)

## 2. Key concepts
Please refer to the following Fundamentals to learn the key concepts of both patterns

- [eMagiz API Gateway](../../docs/fundamental/fundamental-api-gateway-introduction)
- [eMagiz Messaging](../../docs/fundamental/fundamental-event-streaming-introduction)

##### Theory
  
## 3. Considerations for selecting Messaging or Event Streaming

The following sections are helpful to understand what things to consider in selecting the right pattern. 

- **Asynchronous**
	- Both patterns are asynchronous in nature. In case a synchronous message is the right choice, pelase refer to the relevant microlearning that compares messaging and API gateway
	
- **Data**
	- Event Streaming solutions are typically used in large volumes of data whereby each message is relatively small. A typical example is an IoT data stream, but you can use Event Streaming for order, confirmations or other data collections. There is a maximum value for each message on a topic of 1Mb
	- Messaging can handle larger messages although 1 Mb message are the average that eMagiz considers. In case larger messages exist, Messaging would be a better option
	
- **Online vs. offline**
	- For Messaging, the delivering and receiving system need to be online with high availability ratio's in order to process the messages
	- For Event Streaming, producers and consumers can choose their own downtime and for small intervals where messages are not produces or consumed
	
- **Contract & communication**
	- Messaging required a fixed contract between the message definitions that are exchanged. A change of definition would result in validation issues and therefore more communication is required
	- Event Streaming has a more loosly character in a sense that the producer defines the message that is send and publishes it to the consumer. COnsumer can then consume the message and decide how to process the message
	
- **Technical disqualifiers**
	- Use Event Streaming requires the produces and the consumer to have the technical capability to produce and consume messages on a Kafka topic. 
	- Messaging allows to receive and send messages via many more protocols such as REST, SOAP, File pickup, etc. Please note that eMagiz Messaging can also produce and consume messages from and to topics which can help to support the use of event streaming
	
- **Data Storage**
	- In the Messaging pattern, no data is stored and the data is in full transit
	- In the Event Streaming pattern, data is persisted for a short time in a storage location. The data is still considered to be in  transit, but making choice where data is persisted too often with minimal change to the message could impact data storage. eMagiz has licensed limits for data storage in Event Streaming.
	

##### Practice

## 4. Assignment

There is no assignment for now in this microlearning

## 5. Key takeaways

- There are a set of considerations to make decisions for event streaming vs. messaging
- Make sure to read the eMagiz Fundamentals properly before taking this section into account in your project

##### Solution

## 6. Suggested Additional Readings

Take a moment to read the following link https://emagiz.github.io/docs/usecase/index_academy_usecase_pattern_discovery

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video that accompanies this microlearning.

</div>
</main>
</div>
</div>