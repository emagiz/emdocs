#How to upgrade a message bus completely or partially to eMagiz 5 

Background on Artemis with a "reason why" at the end

In order to upgrade to Artemis, 4 conditions must be met:




1) Spring Integration from 2 to 4: the flows' current build number is 2 (or lower) and it is still running on Spring Integration 2 (before Nov 2017) but it should be at least 30 because 
the flow is less likely to encounter unforeseen issues. Firstly test your flows and then update them! 
2) Java from 7 to 8: It is needed for solving the next condition. Start updating your Java now (cloud: update to latest template). 
3) eMagiz runtime 5.0.0 or higher: it requires Java 8. Start updating your runtimes now (cloud: update to latest template).
4) enable the Releases widget in the deploy phase: you need to have this widget enabled in order to firstly make a release of your current CREATE phase (which is fully hornetQ at the moment)
 to have a safe hornetQ backup in case there will be any problems while upgrading to Artemis.


The preparation steps for migrating to artemis:

1) Go to the Deploy phase in the bus and click the green button "New release". Now you have a copy of your latest Create phase, "0.0.1: Initial release",  which can be considered 
the hornetQ backup of this process so rename it accordingly.
2) Go to Create -> Settings -> AMQP -> Upgrade to AMQP wizard. Here there are two options of migrating: using the 4 steps wizard or just press the orange button in order to upgrade
the whole bus at once 


The steps for migrating to artemis: 

-> using the "upgrade complete bus at once" button 
	1) Press the orange button. It might take a while until it  finishes upgrading every flow from the bus. 
	2) Go to the deploy phase and refresh the create phase 
	3) Create another release and name it "Artemis" and select it as current release
	4) Go to properties and create the new host and port properties by copying the old ones and replacing 'jms' with 'amqp'
	4) Go to Containers and download and install the runtimes
	5) Go to releases and press the install button and further install all the flows displayed  
	6) Go to runtime dashboard and start all flows
