## User Guide Event Streaming eMagiz

Below the user guide for Event Streaming. In this guide we will focus on the following parts:
-	Using the portal to set up Event streaming possibilities
-	Produce messages on a event stream (Topic) as a part of a message flow in eMagiz
-	Consume messages from an event stream (Topic) as the starting point of a message flow in eMagiz
Should you have any questions, please contact productmanagement@emagiz.com.
Last update: June 30th 2020

## Pre-requisites
- Basic knowledge of the eMagiz platform
- Understanding of Event streaming concepts
- Toggle Feature – Event streaming made available via your partner manager for your environment
- Admin user coupled to eMagiz user account by your partner manager
- eMagiz Managed Kafka cluster available for your project (requires proper licensing and admin configuration by eMagiz)

## Using the portal to set up Event streaming possibilities

In the Deploy phase of eMagiz you will have the option to select Event .

<p align="center"><img src="../../img/howto/userguide-es-0.png"></p>
 
In this screen you will have the following options:
-	Users
-	Access Control Lists (ACL)
-	Topics
-	Schemas
-	Configuration Details
Users
Under the users tab you can create new users, view information on users or delete a user. Every time a new producer or consumer needs to be connected to the Event streaming environment you will have to create a new user via this screen.
When you want to revoke all rights of an existing user you can remove the user via the Delete button. Don’t forget to also remove the ACL and Topic if this is the last remaining user linked to a specific Topic!
 
<p align="center"><img src="../../img/howto/userguide-es-1.png"></p>

### ACL ###
ACL stands for Access control list. This list states which user has which rights on which Topic. In this view you can revoke rights by pressing Delete, view the details of a specific entry in the ACL or Add an ACL entry to the list. Adding an ACL entry to the list is preferable not done here but rather via the Topics tab. The reason for this is that in this way you can link the user and the Topic to each other and on the basis of that automatically create the ACL entry.

<p align="center"><img src="../../img/howto/userguide-es-2.png"></p>

### Topics ###
This is the main page for the hosting of an Event Streaming solution. Under this page you can create Topics, view Topics, delete Topics, fetch messages and monitor traffic on the Topics. 
 
 <p align="center"><img src="../../img/howto/userguide-es-3.png"></p>
 
Let us first look at creating a Topic. For each distinct event you should create a new Topic. For example when you measure both temperature and humidity in a room, the events that are triggered by temperature variations are placed on a separate Topic in comparison to the events that are triggered based on humidity variations.
Creating a Topic can be done by pressing Add Topic and given the Topic a descriptive name (i.e. emagiz.es.acceptance.temperature or emagiz.es.acceptance.humidity), select the user that will receive rights on this Topic and leave the remainder to the default settings made for you. If you want to deviate from these advanced configurations, please first consult the help text provided by eMagiz.
The buttons Monitoring and Fetch messages are created so you can monitor the Topic. Under monitoring you will see how many messages are placed on a Topic and what the size of the Topic is at the moment. Via the fetch messages button you can see which messages have been placed on the Topic, which message has been placed last in the Topic and who produced that message.
Via the Delete option you can remove a Topic altogether. This means no messages can be produced or consumed on that specific Topic. All remaining messages that were still residing on the topic will de deleted also.


### Schemas ###
Just as with the API gateway and with messaging a certain structure or schema needs can be defined. The purpose of a schema in the context of Event Streaming is to let the consumer know how the message they can consume will look like. For event streaming you can define this via the eMagiz portal by adding an AVRO schema. By creating such a schema you can specify for which Topic the message need to adhere to this schema.

 <p align="center"><img src="../../img/howto/userguide-es-4.png"></p>
 
Creating a schema can be done by pressing the Create subject button. In the following screen you enter the name of the subject, which should mimic the name of the Topic and add the schema. If you have trouble creating an AVRO schema please use this easy to use tool to convert a JSON message to an AVRO schema (such as https://toolslick.com/generation/metadata/avro-schema-from-json). This in combination with the example provided in the help text gives you as user an easy way to correctly set up the schema. In future versions, graphical possibilities will be added to create these AVRO schemas without the need to use such external tools.
Apart from creating a schema you can view it, delete it or see the version of a specific schema. By using the compatibility function you can update a schema to a newer version but by setting the compatibility to Backward compatible also make sure that producers and consumers can still exchange messages that adhere to the old structure. eMagiz provides you with several options as shown below.
 

 <p align="center"><img src="../../img/howto/userguide-es-5.png"></p>
 
### Config details ###
This is a read only screen that specifies the technical connections needed to set up the Event Streaming functionality. The bootstrap server information is the part of the screen that is relevant for you as a user if you want to produce or consume messages as a part of a message flow. To learn more about this please see the sections on Produce messages on a event stream (Topic) from eMagiz and Consume messages from a event stream (Topic) via eMagiz


## Produce messages on a event stream (Topic) from eMagiz

Apart from only hosting the Topics on which external parties can produce and consume messages you can also produce messages as a part of an eMagiz message flow. In this way, the eMagiz bus takes on a Hybrid position – both messaging and Event Stream configuration are done. This section will specify how you can make this work.
In the Create phase of eMagiz you can send messages to a Topic. This can be done at any given moment in the integration (entry, onramp, offramp, exit, etc.). For example when a purchase order is executed within your integration landscape you could post the result of this purchase order on the inventory on a Topic for others to consume. 

To produce messages on a Topic you need two components in eMagiz:
1)	A Kafka template. This template sets up the connection between the producer and the server that hosts the Topics. In this component the following things need to be configured:
-	Host and port of the server to which you want to connect to (separated by a semicolon).
-	Security protocol. Default for an server is SSL
-	Client ID. Identifier to determine who produces the messages
-	A keystore (containing a p12 that identifies the client) + including password and type (PKCS12 or JKS)
-	A truststore (containing the ca of the server that authorizes clients) + including password and type (JKS)
 
 
 <p align="center"><img src="../../img/howto/userguide-es-6.png"></p>
 
2)	A Kafka outbound channel adapter. This adapter produces messages on a specific Topic. To make this work you need to configure the following things:

-	The name of the Topic on which you want to produce messages
-	The Partition ID (default is 0) to which you want to write the message. Deviations from the standard can be made if a lot of messages need to be produced. This to reduce the load a consumer needs to process. Or in cases specific messages are only relevant for certain consumers.
-	Link to a Kafka template

  
 <p align="center"><img src="../../img/howto/userguide-es-6.png"></p>
 
## Consume messages from a event stream (Topic) via eMagiz

Apart from only hosting the Topics on which external parties can produce and consume messages you can also consume messages as a part of an eMagiz message flow. This section will specify how you can make this work.
In the Create phase of eMagiz you can receive messages from a Topic. This could form the starting point of your integration. For example, buying certain products leads to an event telling several systems that new raw materials need to be purchased and new goods need to be produced
To consume messages from a Topic you need two components in eMagiz:
1)	Kafka message listener container
-	Host and port of the server to which you want to connect to (separated by a semicolon).
-	Security protocol. Default for an server is SSL
-	Group ID (Cluster ID). Identifier of the group / cluster to which the Topic belongs.
-	A keystore (containing a p12 that identifies the client) + including password and type (PKCS12 or JKS)
-	A truststore (containing the ca of the server that authorizes clients) + including password and type (JKS)
   
 <p align="center"><img src="../../img/howto/userguide-es-7.png"></p>
 
 
2)	Kafka message driven channel adapter
-	Link to the Kafka message listener

  
 <p align="center"><img src="../../img/howto/userguide-es-8.png"></p>
 


