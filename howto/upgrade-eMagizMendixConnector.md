# STEP PLAN INSTALLATION EMAGIZ MENDIX CONNECTOR

To get a new version of the EMagiz Mendix Connector in a Mendix app, the following steps need to be performed.  

##  1. Download the eMagiz Mendix connector
   - The EMagiz Mendix connector is Download via EMagiz. Log in and then go to one of the busses you have access to.    
   - Under the Step "Deploy | On Premises | Runtime Downloads "is the EMagiz Mendix connector to download. It is important that you look at the column Mendix version. It must correspond to the Mendix version of the project where you want to use the EMagiz Mendix Connector. If you do not do this then the connector will not work.  
   
<p align="center">
  <img  src="resources/emc-runtime-downloads.png"> 
</p>

##  2. Importing eMagiz Mendix connector  
   - In the next step The connector is imported into the correct Mendix project. Open the Project. In the Project Explorer, choose Right-click and the option "Import module package..."
   
<p align="center">
  <img src="resources/emc-import-mx-app-module.png"> 
</p>

   - Select the appropriate EMagizMendix connector.

**Please note:**  
Because it is already present, you get a question that you choose the Override option.

##  3. Configuration 
- Afterstartup/before shutdown
- Rights
- Navigation
- Constants
- Webservices cloud / Webservice user / 
- Request handler

##  4. Usage  
- Deployment/updaten flows
- Starting/stopping flows
- Explanation User Interface
- Version Numbering

##  5. Log errors/warnings 
There are several situations where you get errors/warnings in your project as a result of the InstallationUpdating the EMagiz Mendix connector. An example of this is WAnneer The Mendix project has multiple languages after the import you will receive multiple errors/warnings. These are easy to solve by following the steps.

<p align="center">
  <img src="resources/emc-language-operations.png"> 
</p>

<p align="center">
  <img src="resources/emc-language-operations-2.png"> 
</p>  

##  6. eMagiz cleanup tool
##  7. Cleanup project directory
