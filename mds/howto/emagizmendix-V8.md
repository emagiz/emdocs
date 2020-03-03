## Introduction

This document is valid for all eMagiz Mendix connector versions that are currently supported. That includes the most recent addition that support Mendix version 8, which brings some changes in the way the Connector is used.

Last update on March 6th, 2020

## Positoning of the eMagiz Connector for Mendix 8 package

This packages has been created to support clients that are moving towards Mendix 8 in their environment. The latest version of eMagiz ha bee upgraded to use AMQP queues, which effectively means that direct connections from Mendix to onramp and offramp queues can be made. This has a positive effect as less effort is required in Mendix to interact with eMagiz and there is an easier management of the environment as only the infra flows need to be deployed (no exit and entry flows managed in Mendix).

To take benefit from this, eMagiz has released this version to take the first steps in this direction. Below are some more details and instructions to use this new version. Please read these carefully.

Please find the package on the usual location: Under Deploy --> On-premise --> Runtime downloads tab

## Comparing eMagiz Mendix connector

| Mendix V6/V7 Connector| Mendix V8 Connector|
| ------ | ------ |
| Messages received in XML  | Messages received in XML, JSON or Data Model|
| Web service required to receive messages. For sending messages, a Request Handler in the Mendix model is required | Direct connection to the eMagiz queue (onramp/offramp) made via Java Action|
| Each flow (exit, entry and infra) needs to be deployed | Only infra flow needs to be deployed once, microflows connected to the queues directly |
|Incoming webservice <p align="center"><img  src="../../img/howto/eMM Connector - Old view webservice.png"></p>| Microflow - Java action details<p align="center"><img  src="../../img/howto/eMM Connector - New view webservice.png"></p>|

## Best practices eMagiz Connector for Mendix 8

- Make one microflow to register all queues. Link it to the After Startup microflow
- Use supplied Java actions in the eMagiz Mendix connector to set up the connections
- Use Alerting to inform Support / Customer when a Job Failed. Can be done based on logging created by the data pipeline

## Short instruction video

Please refer to the eMagiz Community page, under Academy to find the session where the eMagiz Mendix Connector is introduced, and where a short example is worked out. In the Module eMagiz ABL Block 1 (Beta sessions) you can find this session.

## Key notes in using this package

Please take care of the following items
- These 2 libraries could cause issues with the current version of the Connector - please evaluate the necessity of these. 
  - lib x
  - lib x

## Planned improvements for 2020
These are the items that the eMagiz team is planning to improve in the course of 2020
- eMagiz Portal changes as related to the display & configuration of this Connector: 
    - Register Mendix version
    - Remove specific older items from the eMagiz portal (e.g. Request Handler)		
    - Auto download correct EMC version
    - “Download single file” only contains infra component	
- Remove infra component all together 
