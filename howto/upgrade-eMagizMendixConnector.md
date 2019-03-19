# STEP PLAN INSTALLATION EMAGIZ MENDIX CONNECTOR

To get a new version of the EMagiz Mendix Connector in a Mendix app, the following steps need to be performed.  

##  1. Download the eMagiz Mendix connector
   - The EMagiz Mendix connector can be downloaded via EMagiz. Log in and then go to one of the busses you have access to.    
   - Go to **Deploy -> On Premises -> Runtime Downloads** the EMagiz Mendix connector can be downloaded. It is important that you look at the column Mendix version. It must correspond to the Mendix version of the project where you want to use the EMagiz Mendix Connector. If you do not do this then the connector will **not** work.  
   
<p align="center">
  <img  src="resources/emc-runtime-downloads.png"> 
</p>

##  2. Importing eMagiz Mendix connector  
   - In the next step the connector is imported into the correct Mendix project. Open the Project. In the Project Explorer, right-click and choose the option "Import module package..."
   
<p align="center">
  <img src="resources/emc-import-mx-app-module.png"> 
</p>

   - Select the appropriate EMagizMendix connector.

**Please note:**  
If it is already present, you get a question where you choose the **override** option.

##  3. Configuration 
- Afterstartup/before shutdown
- Rights
- Navigation
- Constants
- Webservices cloud / Webservice user
- Request handler

##  4. Usage  
- Deployment/updating flows
- Starting/stopping flows
- Explanation User Interface
- Version Numbering

##  5. Possible errors  

There are several situations where you get errors/warnings in your project as a result of the installation/updating the EMagiz Mendix connector.

  - **Log errors/warnings**
  
 An example of this is when The Mendix project has multiple languages. After the import you will receive multiple errors/warnings. These are easy to solve by following the steps.

<p align="center">
  <img src="resources/emc-language-operations.png"> 
</p>

<p align="center">
  <img src="resources/emc-language-operations-2.png"> 
</p>  



  - **Layout errors that can be solved with the eMagiz cleanup tool**
  
Another example is the layouts. These can be solved by choosing the layouts that are used within your project.  

<p align="center">
  <img src="resources/emc-display-project-directory.png"> 
</p> 

The cleanup is in the project directory Under the Resource folders.

<p align="center">
  <img src="resources/emc-cleanup-tool.png"> 
</p> 

Click right mouse button (or double click) For "Openings with | Java™ Platform SE Binary

<p align="center">
  <img src="resources/emc-open-cleanup-tool.png"> 
</p> 

After performing this action it is good to check the userlib for verification. This can be based on the following steps. First open your project folder (see below)

<p align="center">
  <img src="resources/emc-display-project-directory.png"> 
</p>

Then navigate to Userlib. In this userlib, there should only be one reference to a version of the EMagizMendixConnector. (see below)

<p align="center">
  <img src="resources/emc-mendix-jar-file.png"> 
</p>

For reference, all JAR files using the EMagizMendixConnector (version 2.4.1):  

<p align="center">
  <img src="resources/emc-all-jar-files.png"> 
</p>

  - **Cleanup the project directory to avoid other problems**

The last step is to clean up the project directory and then committing your customization. Ideally, you perform all of these actions in a single commit so that you can perform a rollback and so that you can easily isolate any problems.

<p align="center">
  <img src="resources/emc-mendix-clean-project-directory.png"> 
</p>  

##  6. Best practices  

 - Configure startup time
 - Communication in conjunction with Mendix Inbound/outbound Web services
 - Conflicting userlib AppStore Modules
 - Tracing WebServices Lognode at debugging
 - Deployments – updates request handler
 - Restart
 - Stop
 - Start
 - OnDersteunde Mendix Versions
 - What to consider
 - Multithreading
 - Error handling
 - Retry mechanisme