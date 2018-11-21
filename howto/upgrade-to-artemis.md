# How to upgrade a message bus completely or partially to eMagiz 5 

# 1. Introduction

This tutorial presents the possibilities of migrationg a bus from hornetQ to Artemis.


# 2. Requirements

In order to upgrade to Artemis, 4 conditions must be met in order:

2.1) Spring Integration 4: It is recommended that all flows have the build number 32. All flows with a build number 22 or lower are not going to be able to upgrade and the ones between 22 and 32 are more errorprone. Firstly test your flows and then update them!

2.2) enable the Releases functionality in the deploy phase (this can be done by contacting your partner contact): you need to have this widget enabled in order to firstly make a release of your current CREATE phase (which is fully hornetQ at the moment) to have a safe hornetQ backup of the Create phase in case there will be any problems while upgrading to Artemis.

2.3) Java 8: It is needed for meeting the next requirement. Start updating your Java now or update to latest cloud template (R3 for AWS or instance template >= 20 for Root) if you run in cloud slots. 

2.4) eMagiz runtime 5.0.0 or higher: it requires Java 8. Start updating your runtimes now by downloading the latest version of the runtime from the eMagiz portal if you have on-premise installations or update to latest cloud template .

  **When you think you meet these requirements, ask your partner manager to allow the migration.**
 

# 3. Preparation steps 

3.1) **Using the [releases documentation](https://github.com/emagiz/emdocs/blob/master/howto/deploy-releases.md)** create a copy of your latest Create phase which can be considered the hornetQ backup of this process so rename it accordingly. Also, this should be promoted to the other environments (such as acceptance and production) in order to have a backup of the process in those environments as well. It can be done by using the point 2.4 from  [this documentation](https://github.com/emagiz/emdocs/blob/master/howto/deploy-releases.md)

3.2) **Go to** properties and create the new host and port properties by copying the old ones and replacing 'jms' with 'amqp'. The values that should be used for the ports are 8444 for the backup server and 8443 for the other.

3.3) **Go to** Create -> Settings -> AMQP -> Upgrade to AMQP wizard. Here there are two options of migrating: using the 4 steps wizard or just press the orange button in order to upgrade the whole bus at once 


# 4.The steps for migrating to artemis: 

 **4.1 Using the "upgrade complete bus at once" button**

4.1.1) **Press** the orange button. It might take a while until it finishes upgrading every flow from the bus. 

4.1.2) **Go to** the deploy phase and refresh the create phase. 

4.1.3) **Create** another release based on the refreshed create phase and name it "Artemis". Aferwards, select it as current release.

4.1.4.1) (If you run on premises) **Go to** Containers and download and install the runtimes.

4.1.4.2) (If you run in cloud slots) **Go to** ??? 

4.1.5) **Go to** releases and press the install button and further install all the flows displayed.  

4.1.6) **Go to** each container in the runtime dashboard and start the flow(s).


 **4.2 Using the "step by step" wizard** 

4.2.1) **Press** the first button, "Step 1: Upgrade JMS server(s)", and wait for the process to finish

4.2.2) **Go to** the deploy phase and refresh the create phase. 

4.2.3) **Create** another release and name it "Artemis: Step 1" based on the create phase and select it as current release.

4.2.4) **Go to** Containers and download and install the runtime(s) corresponding to the containers upgraded

4.2.5) **Go to** Releases and press the install button and further install all the flows displayed.

4.2.6) **Go to** each container in runtime dashboard and start the flow(s).

4.2.7) **Repeat steps 1-6** for the first three steps of the migraton wizard from the eMagiz portal. Name all the releases according to 
the step that has been done in that stage.

4.2.8) **Press** the fourth button, "Step 4: Remove backward compatibility of JMS server", and wait for the process to finish

4.2.9) **Go to** Runtime dashboard and check if every flow is still active.
