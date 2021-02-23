# Interpreting queue statistics

In this microlearning, we will focus on how you can read the information available on queue level for all integrations that use the messaging pattern.

Should you have any questions, please contact academy@emagiz.com.

- Last update: February 23th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around how you can read the information in the queue statistics and what you can learn from it.
By queue statistics we mean: Information on queue level that helps you to interpret the data that is passing on that queue

There are four parts to the queue statistics:
- Total messages in queue
- Total messages added to queue
- Number of consumers
- Data measurements

## 3. Interpreting queue statistics

In many cases, you want to validate your assumptions by checking the queue statistics. The queue statistics section in eMagiz is divided into four parts:

- Total messages in queue
- Total messages added to queue
- Number of consumers
- Data measurements

For example, when you want to verify how many messages have arrived on a certain queue within a certain time window you can use the queue statistics overview for this.

Below we will delve into each of these four parts and explain a bit more about them. 
That way you can use the queue statistics to interpret what happened within your messaging flows at any given moment

### 3.1 Total messages in queue

When you navigate to the Create phase of eMagiz you have the option to add integrations to Create. This button is located at the right bottom of your screen.
If you click on this button you will arrive at a page that looks something like this:

<p align="center"><img src="../../img/microlearning/ml-create-your-topic--add-integrations.png"></p>

If you want to create a certain topic you simply select the checkbox that is still available (white background, green border) for both the producing and consuming side.

<p align="center"><img src="../../img/microlearning/ml-create-your-topic--add-integrations-selected.png"></p>

The moment you are satisfied with your choice you can Press Save Selection to tell eMagiz that you want to Create the topic(s) you have just selected.

### 3.2 Register the topic on the cluster

After you have created the topic in Create you can access the topic information of your topic with the help of the context menu on topic level.
If you go to the Create overview of the Stream pattern you can right-click on the topic itself to retrieve the topic information.

<p align="center"><img src="../../img/microlearning/ml-create-your-topic--es-create-topic-info.png"></p>

In the pop-up that is opened when you select the option, you can see the details of your configuration. This name will be used by eMagiz to register the topic on the cluster.

<p align="center"><img src="../../img/microlearning/ml-create-your-topic--es-create-topic-info-pop-up.png"></p>

To tell eMagiz to register the cluster navigate to Deploy -> Releases. Here you can open the context menu on the Create phase

<p align="center"><img src="../../img/microlearning/ml-create-your-topic--es-deploy-context-menu-create-phase.png"></p>

In this context menu, you have the option called Batch Update. By selecting this option eMagiz will automatically register all new topics to your cluster.

You can check the results of this action in the Event streaming section in Deploy by opening the Topic tab.

<p align="center"><img src="../../img/microlearning/ml-create-your-topic--es-deploy-event-streaming-config-topic-tab.png"></p>


## 4. Assignment

Add your topic to Create. This assignment can be completed with the help of the Topic you have created/used in the previous assignment on your (Academy) project.

## 5. Key takeaways

- It is easy to create a topic in eMagiz, simply select the topic you want and press Save Selection
- Don't forget to set up your infra the first time you start working with Event Streaming
- After you have created your topic you can register the topic via Deploy.

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz when executing these actions.

## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned.

<iframe width="1280" height="720" src="../../vid/microlearning/microlearning-create-your-topic.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>