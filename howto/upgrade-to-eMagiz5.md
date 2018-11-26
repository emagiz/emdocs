# How to upgrade a message bus completely to eMagiz 5 

## 1. Introduction

This tutorial presents the possibilities of migrating a bus from eMagiz 4 to eMagiz 5.


## 2. Requirements

In order to upgrade to eMagiz5, 4 conditions must be met in order:

2.1) Spring Integration 4: It is recommended that all flows have the build number 32. All flows with a build number 22 or lower are not going to be able to upgrade and the ones between 22 and 32 are more errorprone. Firstly test your flows and then update them!

2.2) enable the Releases functionality in the deploy phase (this can be done by contacting your partner contact): you need to have this new way of deploying enabled in order to firstly make a release of your current CREATE phase (which is using eMagiz4  at the moment) to have a safe eMagiz4 backup prior to the migration in case there will be any problems while upgrading to eMagiz5.

2.3) Java 8: the new framework works only from java 8 or higher. Java 8 is required for updating to the latest runtime version.

2.4.1) For on-premise environments only updating your java is not enough, you also need to reinstall the eMagiz5 runtime. Start updating your runtimes now by downloading the latest version of the runtime from the eMagiz portal if you have on-premise installations. 

2.4.2) For environments running in cloud you just need to update to the newest template (R3 for AWS Cloud or instance template >= 20 for Root Cloud).

  **In order to proceed further with the migration, a check on meeting with the bus partner contact is needed.**
 

## 3. Preparation steps 

3.1) **Using the [releases documentation](https://github.com/emagiz/emdocs/blob/master/howto/deploy-releases.md)** create a copy of your latest Create phase for every environment(testing, acceptance and production) which can be considered the eMagiz 4 backup of this process so rename them accordingly( e.g. eMagiz4 backup). Make sure that each backup contains the versions of the flows that are currently running on that environment. It is recommended that the acceptance and production environments are the same. It can be done by using the point 2.4 from  [this documentation](https://github.com/emagiz/emdocs/blob/master/howto/deploy-releases.md)

3.2) **Make sure** the runtimes you would like to upgrade are running before starting the migration process.

3.2) **Go to** Create -> Settings -> Message bus settings and copy the technical name of the bus. Then go to Deploy -> Properties and create 2 (or 4 if you have a failover bus) new properties for the host and port of the jms server(s). They should all be global, of type string and have the following content:

3.2.1) name: technical name + “.amqp01.host”, value: amqp01.cloud000x.emagizcloud.com (in order to replace the ‘x’ in this value you need to contact your partner contact)

3.2.2) name: technical name + “.amqp01.port”, value: 8443
 
3.2.3) (ONLY IF YOU HAVE A FAILOVER BUS) name: technical name + “.amqp01b1.host”, value: amqp01b1.cloud000x.emagizcloud.com (in order to replace the ‘x’ in this value you need to contact your partner contact)

3.2.4) (ONLY IF YOU HAVE A FAILOVER BUS) name: technical name + “.amqp01b1.port”, value: 8444

3.3) **Go to** Create -> Settings -> AMQP -> Upgrade to AMQP wizard. It is recommended to upgrade the bus by using the method 4.1. If it does not succeed, then it is recommended to make use of the method from 4.2.


## 4.The steps for migrating to eMagiz 5: 

<!--- Before choosing one of the two ways of approaching this migration you should take into consideration the following aspects: 
- available time for completing the migration process
- size of the bus
- failover or normal 
- type of deploying premises: local, cloud slot or both
- affordable down time of the bus (ask your partner contact for the estimated value)
--->


### 4.1 Using the "upgrade complete bus at once" button

4.1.1) **Go to** Deploy -> Releases and create a release based on the backup created during 3.1) named "eMagiz 5 migration".

4.1.2)  **Go to** Create -> Settings -> AMQP -> Upgrade to AMQP wizard. Press the "upgrade complete bus at once" button. It might take a while until it finishes upgrading every flow from the bus.  If it does not succeed, try again using the method from 4.2, starting with the point 4.2.2).

4.1.3) **Go to** Deploy -> Releases and click "update to latest versions". Afterwards you can press the install button and further install all the new versions of the flows displayed.

4.1.4) **Go to** each container in the runtime dashboard and start the flow(s) in the following order:

4.1.4.1) If you have a failover bus: Firstly start the live JMS server, amqp01, and secondly the back up server, amqp01b1. In all other cases just start the jms server before any other flows.

4.1.4.2) Container(s): if you have multiple containers, you can use any order.

4.1.4.3) Connector(s): if you have multiple connectors, you can use any order.

4.1.5) **Go to** Runtime dashboard and check if every flow is still active.


### 4.2 Using the "step by step" wizard 

4.2.1) **Go to** Deploy -> Releases and create a release based on the backup created during 3.1) named "eMagiz 5 migration".

4.2.2) **Press** the button "Step 1: Upgrade JMS server(s)", and wait for the process to finish.

4.2.3) **Press** the button "Step 2: Upgrade process container(s)" and wait for the process to finish.

4.2.4) **Press** the button "Step 3: Upgrade connectors" and wait for the process to finish.

4.2.5) **Press** the button "Step 4: Remove backward compatibility of JMS server" and wait for the process to finish.

4.2.6) **Go to** Deploy -> Releases and click "update to latest versions". Afterwards you can press the install button and further install all the new versions of the flows displayed.

4.2.7) **Go to** each container in the runtime dashboard and start the flow(s) in the following order:

4.2.7.1) If you have a failover bus: Firstly start the live JMS server, amqp01, and secondly the back up server, amqp01b1. In all other cases just start the jms server before any other flows.

4.2.7.2) Container(s): if you have multiple containers, you can use any order.

4.2.7.3) Connector(s): if you have multiple connectors, you can use any order.

4.2.8) **Go to** Runtime dashboard and check if every flow is still active.
