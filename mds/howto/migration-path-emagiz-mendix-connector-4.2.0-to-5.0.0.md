## Migration Path - eMagiz Mendix Connector 4.2.0 -> 5.0.0

Below you will find a document describing the migration path to upgrade your eMagiz Mendix Connector from version 4.2.0 to 5.0.0.
In case you want to implement an eMagiz Mendix Connector in a new Mendix project, ensure that you retrieve the latest version from the Mendix Marketplace as that will guarantee that the newest version is immediately chosen so you can implement it.

Should you have any questions, please get in touch with productmanagement@emagiz.com.
Last update: November 25th, 2021

## Pre-requisites
- Basic knowledge of the eMagiz platform
- Understanding of eMagiz Mendix Connectors
- A need to upgrade from 4.2.0 to 5.0.0

## 1. Retrieve latest eMagiz Mendix Connector

The first step would be to download the latest version of the eMagiz Mendix Connector. You can do this via the marketplace of Mendix, or you can navigate within your eMagiz model to Deploy -> On-premises and open the tab Runtime Downloads to download the latest version that works for the Mendix version your project is running in.

<p align="center"><img src="../../img/microlearning/novice-mendix-connectivity-update-emagiz-mendix-connector--emc-download-screen.png"></p> 

## 2. Update the eMagiz Mendix Connector

Please read the following [microlearning](../microlearning/novice-mendix-connectivity-update-emagiz-mendix-connector.md) as this microlearning details how you should update your eMagiz Mendix Connector.

## 3. Specific configuration

The following points warrant additional actions on your part as they are needed to make the solution work within version 5.0.0

- The after startup microflow within the module has been renamed. Ensure that you refer to the new and correct after startup microflow within your own after startup microflow or directly from the Project settings. Note that the after startup microflow is now called AfterStartup
- The register microflow is not needed anymore in version 5.0.0. To make the solution work in 5.0.0, you need to change the exit flows in the portal to define the correct information. 
    - For asynchronous exits you can check out this [microlearning](../microlearning/intermediate-mendix-connectivity-calling-an-asynchronous-webservice-in-mendix.md) on how to exactly configure the exit flow correctly
    - For synchronous exits you can check out this [microlearning](../microlearning/intermediate-mendix-connectivity-calling-a-synchronous-webservice-in-mendix.md) on how to exactly configure the exit flow correctly
- The XML Configuration overview has returned (XmlConfiguration_Overview). So make sure that the relevant role(s) can view this overview in case a migration needs to be performed, or a manual download is needed.