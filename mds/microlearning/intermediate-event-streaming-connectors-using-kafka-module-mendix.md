<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-event-streaming-connectors-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Using Kafka Module in Mendix

In this microlearning, we will focus on how you can utilize the Kafka Module from eMagiz as available via the portal to consume and produce data from topics managed within the eMagiz Kafka Cluster.

Should you have any questions, please contact academy@emagiz.com.

- Last update: April 14th, 2021
- Required reading time: 10 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Basic knowledge of the Mendix platform
- Mendix project in which you can test this functionality
- Kafka cluster you can use to test against.
- Access to the eMagiz Event catalog in order to obtain the required Keystore & Truststore.
	- To learn more about the eMagiz Event Catalog please refer to the microlearning which can be found here [eMagiz Event Catalog](crashcourse-eventstreaming-catalog.md)

## 2. Key concepts
This microlearning centers around using the Kafka module of eMagiz in Mendix.
By using, in this context, we mean: Being able to produce and consume data to and from topics that are managed within an external Kafka Cluster, such as the eMagiz Kafka Cluster.

By knowing how you can easily set up Mendix to consume and produce data from and to topics you have the option to better transport large volumes of data between several systems (i.e. two Mendix applications).

Producing data on a topic means that the external system, in this case, Mendix, writes data to a pre-defined topic where the data is stored temporarily to make sure that the data can be consumed by one or more other systems.
Consuming data from a topic means that the external system, in this case, Mendix, reads data from a pre-defined topic where the data is stored temporarily.

##### Theory

## 3. Using Kafka Module in Mendix

To use the Kafka Module in Mendix you need to be able to do at least the following:
1. Set up a connection to the external Kafka Cluster (i.e the eMagiz Kafka Cluster) from Mendix
2. Configure a Producer that can write (publish) data to a topic and/or configure a Consumer that can read (listen) data from a topic

When you have configured these steps you would have to think about how you want to transfer data from and to your data model. 
That part is excluded in this microlearning as that focuses solely on how you build microflows in Mendix. 
It is good to notice that the Kafka Module comes with some good examples of microflows that you can use as a starting point. 
These examples can be found in the _USE_ME folder of the Mendix module

### 3.1 Initial Configuration Kafka Module

The first step is to set up the connection to an external Kafka Cluster. Before we can configure anything we first need to retrieve the correct Mendix Modules from the Mendix App Store to which we have a dependency.

#### 3.1.1 App Store Modules needed - Dependency

You will need the following App Store Modules (if you do not yet have them in your Mendix project):

- MxModelReflection
- LibraryLogging
- Encryption

If you have not yet imported the Encryption module into your project ensure that you define the constant called EncryptionKey based on the information as specified by Mendix. Special attention is warranted for the length of the key as this length can vary based on the version of the Encryption module that you use.
Furthermore, note that the MxModelReflection can be used to make your microflows accessible as an on receive microflow when you configure your consumer(s).

#### 3.1.2 eMagiz Kafka Module

The eMagiz Kafka Module is made available via the portal (in a similar manner as with the eMagiz Mendix Connector). We will work towards making the module available in the Mendix Store as well.
If you have trouble finding the correct module please contact productmanagement@emagiz.com.

#### 3.1.2 Making the configuration page accessible

After you have imported those four App Store Modules within your project you can take the next step. 
Within the Kafka Module there is a microflow called OpenAdministration, make sure an admin can reach this microflow as this is the starting point for the rest of the configuration.

#### 3.2 Set up a connection to the external Kafka Cluster

When you run your project, call the microflow. The microflow will lead you to the following page.

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--kafka-admin-overview.png"></p>

This page consists of four tabs. The first tab documents the steps you need to take. The second tab is for the server configuration and to create a producer config. The third tab is for a consumer config. The fourth and last tab is to test your connection to the cluster. In this segment, we will focus our attention on setting up the connection between Mendix and the Kafka cluster. This is a prerequisite for the configuration of producers and consumers and a working solution.

To set up the general settings first navigate to the tab called Configuration Details. This will lead you to the following overview.

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--kafka-admin-overview-configuration.png"></p>

This overview holds all generic configuration elements that are needed to set up a connection to a Kafka cluster. Under the advanced tab, you will see the detailed configuration. You do not have to change any of these settings.

The settings you do need to change/fill in however are:

- bootstrap servers (Ask your implementation contact that manages the Kafka cluster for the correct URL)

If you have done so you can continue on this page by filling in the SSL details. In this second part of the overview, we define the Truststore and Keystore that are needed to authenticate ourselves with the Kafka Cluster.

Ask your implementation contact for the relevant Keystore and Truststore belonging to your user (including passwords).

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--kafka-admin-overview-ssl.png"></p>

If you have received the Keystore and Truststore you can upload them and fill in the password. 
Remember, it is a best practice to ensure that the private key password of the Keystore always matches the password of the Keystore itself.

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--kafka-admin-overview-ssl-filled-in.png"></p>

The moment you are satisfied with your configuration press Save. This will show you a popup that the configuration has indeed been saved.

### 3.3 Configure a Producer

To configure a Producer you navigate to the tab called Configuration Details. On the bottom, you have a section called Producer

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--new-producer.png"></p>

Press the New button and press Save on the screen that is shown to you. The default configuration that is provided works and therefore there is no need to change it. 
The result of this is that you will see a new producer on the Configuration Details page.

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--producer-added.png"></p>


### 3.4 Configure a Consumer

To configure a Consumer you navigate to the tab called Consumers and press the New button.

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--new-consumer.png"></p>

Fill in the relevant information on the General tab:
- Topic(s) from which the consumer will consume data
- Group ID for identification purposes while managing the cluster
- Reference to the on-receive microflow that will handle the incoming data

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--new-consumer-general-filled-in.png"></p>

Once again, the default configuration that is provided under the advanced tab works, and therefore there is no need to change it

If you have done all this press Save. The result of this is that you will see a new consumer on the Consumers tab.

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--consumer-added.png"></p>

#### 3.4.1 Registering a Consumer

After you have configured the consumer you will need to make sure that every time your application starts up the consumer(s) are registered and are listening to whether new data comes in.

To do so make sure that in the after startup microflow of your project you retrieve the consumer(s) you have configured and start them one by one. This can be easily achieved by using the microflow called AfterStartUpConsumersMicroflow which you can find in the _USE_ME folder of the Kafka Module as part of your own after startup microflow.

<p align="center"><img src="../../img/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix--consumer-registered.png"></p>

### 3.5 Testing the connection

To test the connection (for both the consumer as producer config) you can use the Explore and Publish tabs that are available under the Playground tab.
To test the configuration of the consumer navigate to the Explore tab and press Retrieve Topics. If Mendix returns one or more topics you know that the consumer configuration is done correctly.

To test whether your producer configuration is correct you will have to navigate to the Publish tab. In here you need to select the Producer config, 
enter the topic to which you want to Publish data and enter a message payload that you want to publish on that topic.

If you have done so press the Publish button. If everything is configured correctly you will receive a popup saying Message published in partition x at offset y! where x and y are dynamically determined by Mendix.

Congratulations, you have successfully configured Mendix to produce and consume data from and to topics registered on an external Kafka cluster.

##### Practice

## 4. Assignment

Set up a connection between your Mendix application and a Kafka cluster and test this connection with the help of the Explore and Publish tabs in the configuration overview.

## 5. Key takeaways

- The starting point is importing the correct (App Store) Modules within your project
- Make sure that your implementation contact has provided you with the relevant information (bootstrap server, Keystore, and Truststore)
- The pre-configured settings Mendix provides you with don't need to be changed
- Testing the configuration and connection can be done via the Explore and Publish tab, found under the Playground tab.

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please see the following links:

- https://www.cloudkarafka.com/blog/2016-11-30-part1-kafka-for-beginners-what-is-apache-kafka.html#:~:text=Apache%20Kafka%20is%20a%20publish,add%2C%20process%20and%20reprocess%20records.
- https://kafka.apache.org/documentation/#topicconfigs
- https://medium.com/@tsureshkumar/sizing-kafka-capacity-needed-for-your-application-fdb6f24f67cd
- https://www.confluent.io/blog/how-choose-number-topics-partitions-kafka-cluster/
- https://kafka.apache.org/intro

##### Solution

## 7. Silent demonstration video

This video demonstrates how you can test whether you have done everything correctly with regards to the assignment and gives you some context on what you have just learned.

<iframe width="1280" height="720" src="../../vid/microlearning/intermediate-event-streaming-connectors-using-kafka-module-mendix.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
</main>
</div>
</div>