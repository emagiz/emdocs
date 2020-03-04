# Introduction

This document is valid for all eMagiz Mendix connector versions that are currently supported. That includes the most recent addition that support Mendix version 8, which brings some changes in the way the Connector is used.

Last update on March 6th, 2020

# eMagiz Mendix Connector

The eMagiz Mendix Connector (EMC) is a Mendix Project module that you can import into your application to make it communicate with eMagiz. To make this connector work correctly, you need to follow the steps presented below. But before starting to follow these steps there are a few things that should be known. Even though the EMC module is imported in the Mendix project, Mendix does not know that it has an EMC inside and neither does the EMC know it is inside a Mendix Project. So, the way to make them communicate is using the webservice calls that Mendix supports. But first, in order for the EMC to be able to communicate with the bus, it needs to know the credentials with which it can connect to the HIP bus so that it can retrieve the list of properties. These credentials are referred as constants below in the steps.

After configuring everything needed for establishing the connection to the HIP services, you will need to create one webservice in order to facilitate the communication between the EMC and the Mendix project. After creating the Webservice, you need to call it from a MF, and in the call, you will need to fill in the credentials with which you are authenticating in the WS. The same credentials you need to fill in the eMagiz HIP (Deploy -> Properties) as the values of the properties corresponding to the request handler.

The last part in setting up the EMC is about enabling access to the WS call from the EMC to the Mendix Project. To do that you will need to create a WebService user in the Mendix Project and enable access for that user through the firewall of the Mendix Project Website.



# Step plan installation eMagiz Mendix Connector

To install the eMagiz Mendix Connector in a Mendix app, the following steps need to be performed.  

##  1. Download the eMagiz Mendix connector
   - The eMagiz Mendix connector can be downloaded via eMagiz. Log in and then go to one of the busses you have access to.    
   - Go to **Deploy -> On Premises -> Runtime Downloads** the eMagiz Mendix connector can be downloaded. It is important that you look at the column Mendix version. It must correspond to the Mendix version of the project where you want to use the eMagiz Mendix Connector. If you do not do this then the connector will **not** work.  
   
<p align="center">
  <img  src="../../img/howto/emc-runtime-downloads.png"> 
</p>

##  2. Importing eMagiz Mendix connector  
   - In the next step the connector is imported into the correct Mendix project. Open the Project. In the Project Explorer, right-click and choose the option "Import module package..."
   
<p align="center">
  <img src="../../img/howto/emc-import-mx-app-module.png"> 
</p>

   - Select the appropriate eMagiz Mendix connector.

**Please note:**  
If it is already present, you get a question where you choose the **override** option.

 
##  3. Configuration 
- **Afterstartup/Before shutdown:** In the Mendix Project, go to Project settings -> Runtime -> for the fields After startup and Before shutdown select the coresponding MFs from the eMagizMendixConnector module.

<p align="center">
  <img src="../../img/howto/emc-after-startup-before-shutdown.png"> 
</p>  

- **Rights** : It is recommended that only the administrator user role has access to the eMagiz Mendix Connector module. In order to do this go to Project Security -> User Roles -> start editing the Administrator User Role -> start editing the Modules roles -> check the box of the eMagiz Mendix Connector module and save. 

<p align="center">
  <img src="../../img/howto/emc-security-rights.png"> 
</p>

- **Navigation page item:** In the Mendix project, go to Navigation -> Click New Item -> fill in the fields as in the image below.

<p align="center">
  <img src="../../img/howto/new-navigation-item.png"> 
</p>

- **Constants:** In the Mendix project, go to project settings -> start editing the active configuration -> Constants -> and add there the following constants from the eMagizMendixConnector module: 

<p align="center">
  <img src="../../img/howto/emc-constants.png"> 
</p>

The values for these constants can be found from the eMagiz HIP: Deploy -> On premises -> Runtime connection settings
<p align="center">
  <img src="../../img/howto/emc-settings-constants.png"> 
</p>  

These constants are used by the Mendix Connector to get access to the HIP services. 

- **Keystore/Truststore:** In the resources folder of the eMagiz Mendix Connector you need to add the keystore and truststore from the eMagiz HIP which can be found in the Resources tab of the Create phase.

 - **Webservice user:** In order for the eMagiz Mendix Connector flow you need to create a user of the consumed webservice in the Mendix project (Administration Overview page) and use these credentials as the values of the username and password values of the connector flow (they can be defined in Deploy -> Properties).

- **Webservices cloud:**  Add the webservice in the cloud which is hosting the Mendix Project. If your project is hosted in the Mendix cloud, you need to enable acces to your network for the URLs which contain '/emagiz-mendix-connector/'. If it runs locally or is hosted in another cloud environment make sure to enable acces the acces in the firewall to the port 5445 or 8443 depending on whether you migrated or not to eMagiz5.
   
- **Request handler** (only for Mendix version prior to V8): 
   - Import xml schema into req handler configuration from the eMagiz HIP. 
   - Create consumed web service in Mx project based on the url 'the url to your MX project' + '/emagiz-mendix-connector/' + 'wsdl' (e.g.: http://localhost:8080/emagiz-mendix-connector/wsdl) and then press 'Import'.  	        
    - Call the webervice in the appropriate MF.   
      **Note:** If you use secrity, in the HTTP headers tab, you need to fill in the credentials that the Request Handler recognizes (the values of the properties used by the request handler set in the Deploy -> Properties in eMagiz HIP)  
                In the SOAP Request Body you need to fill in the values required for the request.  
                In the SOAP Response tab you can opt for storing the response into a variable. To do so, you need to create an import mapping which maps the response of the webservicce into an entity from the domain model.
   

 
## Step by step plan to upgrade the eMagiz Mendix Connector

To get a new version of the eMagiz Mendix Connector in a Mendix app, the following steps from above need to be performed:

   1) [Step 1](upgrade-eMagizMendixConnector.md#1-download-the-emagiz-mendix-connector)
   2) [Step 2](upgrade-eMagizMendixConnector.md#2-importing-emagiz-mendix-connector)
   3) When it comes to [step 3](upgrade-eMagizMendixConnector.md#3-configuration), there is no need to do all the configurations again because they should have already been done when an older version of the connector was installed. So, just to make sure that everything should function correctly, you should go through all the bullet points mentioned in [step 3](upgrade-eMagizMendixConnector.md#3-configuration) and check if there is nothing unusual.
   4) In the best practice document for the eMagiz Mendix Connector there is a list of possible errors and quick fixes for them, so in case you have any errors you should check it because you might find a solution there. It is highly recommended to try the eMagiz Cleanup Tool.
