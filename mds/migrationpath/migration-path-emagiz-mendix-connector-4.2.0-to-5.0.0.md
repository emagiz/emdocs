<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/migrationpath/index_academy_migrationpath_all" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Migration Path - eMagiz Mendix Connector 4.2.0 -> 5.0.0

Below you will find a document describing the migration path to upgrade your eMagiz Mendix Connector from version 4.2.0 to 5.0.0.
In case you want to implement an eMagiz Mendix Connector in a new Mendix project, ensure that you retrieve the latest version from the Mendix Marketplace as that will guarantee that the latest version is immediately chosen so you can implement it.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: March 1st, 2022
- Required reading time: 4 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform
- Understanding of eMagiz Mendix Connectors
- A need to upgrade from 4.2.0 to 5.0.0

## 2. Key concepts

- The exit connector needs to be configured in eMagiz to make the connection work
- The after startup microflow has been renamed
- The configuration will be downloaded automatically
- The flow overview (XML configuration overview) has returned

##### Theory

## 3. Migration Path - eMagiz Mendix Connector 4.2.0 -> 5.0.0

Below you will find a document describing the migration path to upgrade your eMagiz Mendix Connector from version 4.2.0 to 5.0.0.
In case you want to implement an eMagiz Mendix Connector in a new Mendix project, ensure that you retrieve the latest version from the Mendix Marketplace as that will guarantee that the latest version is immediately chosen so you can implement it.

Below we have written down the steps to migrate from the 4.2.0 to the 5.0.0 version of the eMagiz Mendix Connector. Follow these steps carefully to acquire the desired result.

### 3.1 Retrieve latest eMagiz Mendix Connector

The first step would be to download the latest version of the eMagiz Mendix Connector. You can do this via the marketplace of Mendix, or you can navigate within your eMagiz model to Deploy -> On-premises and open the tab Runtime Downloads to download the latest version that works for the Mendix version your project is running in.

<p align="center"><img src="../../img/microlearning/novice-mendix-connectivity-update-emagiz-mendix-connector--emc-download-screen.png"></p> 

### 3.2 Update the eMagiz Mendix Connector

Please read the following [microlearning](../microlearning/novice-mendix-connectivity-update-emagiz-mendix-connector.md) as this microlearning details how you should update your eMagiz Mendix Connector.

### 3.3 Specific configuration

The following points warrant additional actions on your part as they are needed to make the solution work within version 5.0.0

- The after startup microflow within the module has been renamed. Ensure that you refer to the new and correct after startup microflow within your own after startup microflow or directly from the Project settings. Note that the after startup microflow is now called AfterStartup
- The register microflow is not needed anymore in version 5.0.0. To make the solution work in 5.0.0, you need to change the exit flows in the portal to define the correct information. 
    - For asynchronous exits you can check out this [microlearning](../microlearning/intermediate-mendix-connectivity-calling-an-asynchronous-webservice-in-mendix.md) on how to exactly configure the exit flow correctly
    - For synchronous exits you can check out this [microlearning](../microlearning/intermediate-mendix-connectivity-calling-a-synchronous-webservice-in-mendix.md) on how to exactly configure the exit flow correctly
- The XML Configuration overview has returned (XmlConfiguration_Overview). So make sure that the relevant role(s) can view this overview in case a migration needs to be performed or a manual download is needed.

##### Practice

## 4. Key takeaways

- The exit connector needs to be configured in eMagiz to make the connection work
- The after startup microflow has been renamed
- The configuration will be downloaded automatically
- The flow overview (XML configuration overview) has returned
- Migration from 4.2.0 to 5.0.0 requires changes on both sides

</div>
</main>
</div>
</div>