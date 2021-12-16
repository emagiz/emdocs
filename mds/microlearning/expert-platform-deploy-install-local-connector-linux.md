<div class="ez-academy">
	<div class="ez-academy__body">
		<main class="micro-learning">
		<ul class="doc-nav">
			<li class="doc-nav__item"><a href="../../docs/microlearning/expert-solution-architecture-index" class="doc-nav__link">Home</a></li>
			<li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
			<li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
			<li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
			<li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
		</ul>

<div class="doc">

##### Intro

# Install eMagiz runtime on a local server

In this microlearning, we will focus on installing the eMagiz environment locally for Linux.

Should you have any questions, please contact academy@emagiz.com.

- Last update: November 2021
- Required reading time: 5 minutes

## 1. Prerequisites
To install a runtime, please be aware that eMagiz needs an environment that satisfies certain requirements. These requirements can be different depending on your architectural choices. Most common is the connector inside your network and a JMS and container running outside the network. In that case, if you are running only connectors in this environment, please keep the following requirements in mind:

1. OS with support for Java 
2. OS user with granted security rights to run startup services (Windows services) 
3. The correct Java installation (Java 8 SE JRE for example, https://adoptopenjdk.net) with NO automatic updates. OpenJDK 8 is currently the recommended version for eMagiz installations.
4. NTP synchronization – all eMagiz service instances should use the same time and settings. 
5. Access to the internet 
6. Outbound JMS traffic - port 8443 (and 8444 in case of failover situation) - amqp.emagiz.com / cloudXXXX.emagizcloud.com 
	-	General monitoring data to eMagiz iPaaS 
	-	Specific JMS traffic to eMagiz JMS Server 
7. Outbound HTTPS traffic – port 443 – Specific provisioning data- https://rts.emagiz.com/ws/ / https://repository.emagiz.com    
8. Hardware requirements 
	-	Modern CPU  
	-	Enough Disk Space according to sizing calculations 
9. Enough Memory according to sizing calculations
10. JAVA_HOME variable is properly set

## 2. Key concepts
eMagiz uses a runtime component as a container where flow components can be deployed in. There are infrastructure components that act as flows, and there are functional flow components. Furthermore, there are routing and error flows. By deploying these runtimes across various locations across the integration architecture, you can make these flows work as a chain to realize a complete integration.

##### Theory

## 3. Installing eMagiz on Linux

### 3.1 General remarks

1. To run an eMagiz runtime, the OS of the server should support and have Java installed. The current version is Java 8. eMagiz runtimes with version of 5.x or higher only support Java 8. These runtimes will not run on Java 7 or earlier versions. If you are running on Java 7, or if you need to use an earlier version of the eMagiz runtime, please also check ‘Installing an older version of the eMagiz runtime’.
2. Additional to 1), please do NOT allow automatic updates. Updates in Java 8 are installed in a different directory than the earlier version. This causes that with every update, your JAVA_HOME system variable, which ensures that if you use Java you use that version, should be updated manually by every update. If you update automatically, this will cause issues since the JAVA_HOME variable will not properly set after each update. See the following Q&A question to learn more about the importance of JAVA_HOME when using on-premise connectors: https://my.emagiz.com/p/question/172825635700348986. Since it can be though to find a Java version via the Oracle site, you are advised to download your Java version from https://adoptopenjdk.net.
3. By installing a runtime, you also need an OS user with security rights to run startup services. This is required because installing the corresponding service for a connector will make sure that the connector can independently stop or start without any user intervention. This means that if the server (JMS) restarts, no manual actions are required.
4. Each server has a date and time. An eMagiz service instance use the NTP time protocol. The NTP protocol is a networking protocol for clock synchronization based on UTC time. Synchronizing your server with the NTP protocol ensures that eMagiz runtimes ‘talk’ with the same date and time. This ensures that you prevent for example:
	- That you are not able to reach your connector via the Runtime Dashboard
	- That synchronized communication fails due to time out errors caused by out of sync runtimes instead of that a system fails to response.
5. In order to communicate with other runtimes, that are hosted outside your network, you need access to the internet.
6. For your connector to communicate with your JMS server, the on-premise server needs to open its port 8443 (and 8444 in case of failover) for outgoing communication (from the server point of view). Via this port JMS data is communicated. In ensures for example that you are able to reach the connector via the runtime dashboard and that you can see statistics of the runtime in Manage. Via a different port, your connector will communicate with your container and its flows. eMagiz requires that the server opens its port 443 for outgoing information to communicate the actual messages exchanged.
7. The servers itself has requirements as well. Please ensure that the server has a modern CPU, enough diskspace and enough memory.
Most important is that for each runtime at least 1GB of RAM Memory is available. These calculation is made as follows:
	- 500 MB heap memory
	- 192 MB metaspace memory
	- 100 MB overhead The above is the bare minimum needed to run. 
	
As the number of flows running on a connector increases the memory also needs to be increased. The same logic applies to flows that use up a lot of memory because multiple steps are executed within that flow. Both are solid reasons to use 1GB as a general rule of thumb but at the same time always take into account new developments when setting up the sizing.

### 3.2 Download runtime

1.	Download the eMagiz runtime of your connector, JMS, or container via the eMagiz Deploy phase in the Containers tab on the server where it needs to be installed. Please note the environment you want the runtime of. If you download the runtime of the wrong environment you will send to or receive data from the wrong environment. For example, you want to test a flow but by downloading the runtime from the incorrect environment you end up sending data to the Production environment. In the case below, we see that we are downloading a connector runtime ordsys for the Test environment.

![](../../img/howto/runtime-win-install-step4-1.png)

### 3.3 Install the runtime

- Log in via Putty by typing in the host and the port and press load
- When asked for credentials fill in credentials (Be aware, Linux does not accept ctrl+v and does not show the password or an indication of the password). Right mouse click to copy the password and press enter
- Create folder in which the installation needs to happen. Use the following command via Putty: sudo mkdir -p {directory.to.place.file} (When asked for password supply it)
- Download the correct runtime from the correct environment you want to install
- Place the zip file in a folder (probably tmp) from which you can copy it to the directory you created in step 3
- Navigate to the folder in which you placed the zip file (Command is: cd {directory structure}). Copy the zip file to the directory you created in step 3. Command for this is: sudo cp ./{filename of zip} {directory you created in step 3}
- Navigate to the folder to which you copied the zip file (Command is: cd {directory structure}) and unzip the zip file. Command for this is: sudo unzip {name of zip file}
- Check whether the unzip action worked correctly. This can be done by running the command ls -al. This shows all the folder/files in the directory. After conforming, check if you see the directory you expect, the unzip action worked remove the zip file from the folder. This can be done based on the following command: sudo rm -r {name of zipfile}. Check whether removal worked
- Navigate to tmp folder and remove zip from there as well.
- Navigate back to the folder in which you placed the directory you want to install
- Install the service for eMagiz by running “install-service” in the “bin” folder of the unzipped runtime by following the below outlined steps:
	- Check files in “bin” folder are executable (There should be an x when you type: “ls -al” for files: setenv, install-service)(if not then type: sudo chmod a+x setenv install-service karaf shell)
	- Type: “sudo ./install-service”
	- The output of this command shows the command necessary to finish the install as a service. Linux will show you which version of the command you need.
	- Systemd (newer/most systems)(use full path) Type: sudo systemctl enable <INSTALL_DIR>/bin/.service
	- SystemV (older systems)(use full path) Type: sudo ln -s <INSTALL_DIR>/bin/<SERVICE_NAME>-service /etc/init.d/; sudo update-rc.d <SERVICE_NAME>-service defaults
- As administrator, start the eMagiz service (or restart the system, as the service is configured to run “Automatic” at startup):
	- systemd type: sudo systemctl start <SERVICE_NAME>
	- SystemV Type: sudo /etc/init.d/<SERVICE_NAME>-service start
- Use the runtime dashboard in the portal to monitor and control the started runtime (e.g. deploy/undeploy flows).

## 3.4 Update the runtime

Before updating please notice the following:
- Make sure that you know under which account the service is currently running and make sure the new runtime will also start under that account.
- In case you have adjusted the memory please check out the following [microlearning](advanced-solution-architecture-change-memory-runtime-linux.md) on how to make sure that the new runtime will have the same memory

-	Log in via Putty by typing in the host and the port and press load
-  	When asked for credentials fill in credentials (Be aware, Linux does not accept ctrl+v and does not show the password or an indication of the password). Right mouse click to copy the password and press enter
-  	Navigate to the folder in which the current runtime is installed
-	Execute a stop command in linux (see section 3.3 for the exact commands)
-	Uninstall the old runtime (see section 3.3 for the exact commands)
-	Follow the steps in section 3.3 to install the new runtime correctly


### 3.5 Multiple Java versions
When confronted with a situation in which you have to support multiple runtime versions with multiple Java versions. This is mainly the case when both Acceptance and Production connectors are running on the same server on-premise or when you migrate environments in steps. To determine the correct Java version needed for your runtime please see the attached picture detailed under Java runtime and eMagiz runtime compatibility. Be warned: These steps need to be taken before you install a runtime. If you have already installed the runtime please use the correct Linux uninstall command to uninstall the service before proceeding. When confronted with this situation on a live environment please first discuss your actions with CAPE support.

- Log in via Putty by typing in the host and the port and press load
- When asked for credentials fill in credentials (Be aware, Linux does not accept ctrl+v and does not show the password or an indication of the password). Right mouse click to copy the password and press enter
- Navigate to the directory where you have installed the runtime (Command is: cd {directory structure})
- Open the folder related to the runtime you want to change (Command is: cd emagiz_{technicalbusname}-{containertype}-{techincalnameruntime}_{environment}).
- Open the bin folder within your runtime installation (Command is: cd bin)
- Type in the following command: sudo vi setenv.bat
- Type "i" to enter insert mode
- Navigate with the help of the arrow keys to the part of the file that says rem SET JAVA_HOME and change this to SET JAVA_HOME= The Java path refers to the location (path) where Java (8) is installed. Commonly this path will look like: ‘C:\Program Files\Java\jre1.8.x_xxx’ of ‘C:\Program Files\Java\jdk1.8.x_xxx’. Be warned: Make sure no spaces are surrounding the ‘=’ character
- Press ESC and then type ":wq!" then press Enter to save the changes and exit Edit mode. Note: If you would like to exit the file without making any changes press ESC, then type ":q!" and press Enter
- Install the runtime via the steps discussed above

##### Practice

## 4. Assignment

Execute these steps in the training environment. Ensure to have both runtimes active, and see if the flows can be seen active in the Runtime Dashboard

## 5. Key takeaways

- eMagiz has a runtime software component that allows running flows inside. It is generic for all types of flows that exist in eMagiz
- Using the JMS and the Container runtimes created by the eMagiz Portal, you can test your work properly during the microlearning training sessions
- Above instructions are also valid for making the installation on a server where a runtime needs to be deployed locally.
 
##### Solution

## 6. Suggested Additional Readings

N/A

## 7. Silent demonstration video

There is no video available for now

</div>
</main>
</div>
</div>