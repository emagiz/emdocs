# eMagiz platform release considerations

Objective of this document is to understand the considerations around the versioning and updates of the technical components of the eMagiz platform. 

Last update September 12th 2020


## Platform components

**1. Runtime** This is the component to provides the application container where the individual integration flows are deployed into. It's a Java based application container that can run in the Cloud connector, the Local connector or in the Containers that hold the onramps, offramps and routing flows.
**2. Cloud templates** This provides the components such as OS, Java versions, etc. in which the runtime components can operate in. These are Cloud platform specific.
**3. Buildnumbers** Every flow created has a specific build number. This build contains the eMagiz software components that work in conjunction with the flows as configured in the Create phase of the eMagiz Portal. 
**4. eMagiz Portal** Provides web based access to the eMagiz project that contains the Integration model as configured from Capture to Design, and the management components in Deploy & Manage. 


## Key considerations 

1. The eMagiz Portal (https://my.emagiz.com) is updated every 2 weeks to allow for user interface improvements and improvements to the integration model (from Capture to Create). According to the EULA, one can expect a downtime of max. 2 hours at this time of the eMagiz Portal. All other services inside client platform are not affected
2. All buildnumbers released are always backwards compatible with previous build numbers. We are dedicated to ensure client platforms are unaffected by these buildnumbers - as part of the deployment process across Test, Acceptance and Production specifics might be encountered and reported
3. eMagiz plans a major release once per year that involves migration activitities of the current client installation. A separate release should be created and tested to isolate a potential impact in the current installation. eMagiz makes best efforts to make these migrations as smooth as possible with as little effort as possible for client installations
4. The eMagiz platform uses Cloud templates that are manage the Cloud machines where the different runtime components are running on. These Cloud templates are released per Cloud environment such as AWS and are updated between 2 and 3 times per year. The deployment of these can be done via the eMagiz Portal, and per availability zone in case a failover setup has been chosen. The expected downtime for failover setups is none, for single lane setups between 10 and 15 minutes. Messaging traffic is only impacted with a delay - no messages are lost.
5. Each of the components list in the previous section is supported 2 years from the moment the next version is released. 


## Current versions

### Runtimes
**Non-supported versions**
- Version 5.0.0 - released July 27th 2018
--> Expection for client running in the ROOT Cloud environment - this version is still supported for that environment

**Supported versions**
- Version 5.0.2 - released October 19th 2018
- Version 5.0.3 - released May 17th 2019 

### Cloud templates
**Non-supported versions**
- R3
- R4
- R5
- R6

**Supported versions AWS**
- R10 Single Lane
- R12 Single Lane
- R7 Double lane
- R8 Double lane

**Supported versions ROOT**
- V24

### Build numbers
**Non-supported versions**
- All build numbers lower than build 46 (released September 9th 2019)

**Supported versions**
- All build numbers higher than or equal to build 46
