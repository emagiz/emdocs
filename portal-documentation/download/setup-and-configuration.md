# Setup & configuration
https://my.emagiz.com/link/documentation/12

## Deployments
Before an eMagiz configuration can be loaded, eMagiz has to be up and running. There are more ways to deploy eMagiz:
 
  - Mendix application: run your Mendix project
  - As a background process
    - Windows: start with windows service
    - Linux: start with daemon process
  - In a single Java process: run with batch file
 

## Technical requirements

  - Java SE 1.7/1.8

  - OS: 
    - Windows: As long as Java is installed Windows is supported
    - Linux: As long as Java is installed any Linux distribution should work
  - A license: Without a license  the eMagiz runtime will not connect to the eMagiz portal
  - Access to eMagiz flow designer
 
In order to produce a valid eMagiz bus, you can work through the ILM phases, including the eMagiz flow designer to design/build your flows.  After building your bus, you can easily deploy this on your own environment(s). 
 
## eMagiz runtime 

There are different ways to run eMagiz. eMagiz could be integrated in the Mendix runtime or eMagiz could run standalone. Although there are different ways to run eMagiz, they all do the same and that is running eMagiz flows. 
 
## Mendix

The eMagiz runtime is available in different Mendix versions. You can easily import a module mpk in your Mendix project. After importing the mpk, the eMagiz runtime will be available in your module. Configure the module by:
 
  - Add the startup microflow in the eMagiz runtime module to the project startup microflow (according to mendix conventions this would be General.AfterStartup)
  - Add the shutdown microflow in the eMagiz runtime module to the project before shutdown microflow (according to mendix conventions this would be General.BeforeShutdown) 
  - Add the “MainPage” page to your navigation 

After deploying you can import the eMagiz configuration, created in the eMagiz portal, in your Mendix application. 
 
## Standalone
The standalone version of eMagiz can be used by using the karaf.bat and also by installing a windows service. You need to download the eMagiz standalone package and extract this to a file location. Basically the standalone version is a set of directories with the necessary resources to run eMagiz. When you extract the package the following directories will appear:
 
  - Service: Files to install or uninstall the eMagiz service (windows or linux)
  - Resources: Files which are used in the eMagiz configurations like an xsd or xslt
  - Logs: Location with the eMagiz log
  - Libraries: Java libraries which are used by eMagiz
  - Extensions: External libraries which are used by eMagiz
  - Console: Script file to run eMagiz. This file can be edited in order to configure the location of your eMagiz configuration file
  - Config: Location with eMagiz configurations
 

**Location of the eMagiz license key and the eMagiz configurations (deprecated)**

To run the standalone eMagiz the encrypted configuration must be placed in the configuration folder. To run the configuration in the console you have to edit console/run-in-console.cmd. Open it in an editor and point it to your new configuration in the config folder.


_Example:_

    @echo off
    setlocal
    set CONFIG_1=config/first-eMagiz-configuration.enc
    set CONFIG_2=config/second-eMagiz-configuration.enc
    set CONFIG_3=
    set CONFIG_4=
    set CONFIG_5=
    set CONFIG_6=
    set CONFIG_7=
    set CONFIG_8=
    set CONFIG_9=
    set WORKING_DIR=../
    set EXTENSIONS_DIR=extensions/
    set LICENSE_FILE=config/emagiz-license.enc
    set LAUNCHER_JAR=libraries/com.emagiz.launcher-3.16.1.jar
    set INITIAL_MEMORY=64M
    set MAXIMUM_MEMORY=128M
    set MAX_PERM_SIZE=64M
    set JVM_NAME=my.emagiz.app
    set SAAS_URL=
    set SAAS_USERNAME=
    set SAAS_PASSWORD=
    set CUSTOM_LOGBACK_CONFIG=
    set SSL_MAPPINGS_FILE=
    endlocal
    pause
 Run this file to start eMagiz.
