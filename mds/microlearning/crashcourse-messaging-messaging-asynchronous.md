# Messaging Asynchronous

In this microlearning, we will explain the basics of the asynchronous messaging pattern.

Should you have any questions, please contact academy@emagiz.com.

- Last update: February 25th, 2021
- Required reading time: 3 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around the asynchronous messaging pattern in eMagiz.
By asynchronous we mean: The process that processes data without returning to the sending system with an update whether or not the data could be processed successfully.

Key characteristics of asynchronous messaging are:

- Non-blocking. The sender initiates the process and can continue with the next message
- Systems can therefore be loosely connected
- Messages can temporarily be kept in the queue if an end system to which the messages need to be delivered is scheduled to go offline
- Supports one-to-many distribution of messages over the integration landscape

## 3. Messaging Asynchronous

Asynchronous messaging is the pre-dominant option when you implement a messaging integration via eMagiz. 
Key characteristics of asynchronous messaging are:

- Non-blocking. The sender initiates the process and can continue with the next message
- Systems can therefore be loosely connected
- Messages can temporarily be kept in the queue if an end system to which the messages need to be delivered is scheduled to go offline
- Supports one-to-many distribution of messages over the integration landscape

With this method, the sending party supplies the data to eMagiz (via push or pull). eMagiz in turn places the data on a queue (in most cases an onramp queue).

This means that there is no need for the external system to wait for a reply to see what the other system thinks of the message. 
Furthermore, the system can supply the data somewhere and forget about it. eMagiz will ensure that the data is delivered to all systems that want to receive the data.

Because of this loosely coupling between systems via the asynchronous five-layer model in eMagiz you can with ease add supplying and receiving systems and replace them if necessary.

On top of that, it gives you the option to temporarily keep data in a queue if there is a case of scheduled maintenance in one of the receiving systems. 
The sending system can continue to send data to eMagiz and eMagiz will keep it in the queue until the scheduled maintenance is finished.

## 4. Assignment

Analyze an asynchronous messaging flow from entry to exit and determine which queues are used in the process. 
This assignment can be completed with the help of your (Academy) project you have created/used in the previous assignment.

## 5. Key takeaways

- Asynchronous messaging is the pre-dominant option when you implement a messaging integration via eMagiz. 
- Key characteristics of asynchronous messaging are:
	- Non-blocking. The sender initiates the process and can continue with the next message
	- Systems can therefore be loosely connected
	- Messages can temporarily be kept in the queue if an end system to which the messages need to be delivered is scheduled to go offline

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz.
## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned.

<iframe width="1280" height="720" src="../../vid/microlearning/crashcourse-messaging-asynchronous.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>