# How to configure properties in flows

https://my.emagiz.com/link/documentation/3

When creating flows in eMagiz, some messaging components need settings that you do not want to specify 'hard-coded' in the flow. For example, environment specific settings, such as connection URLs and user names/passwords, usually have different values, depending on where the flow is used. When testing such a flow you need different values compared to running the same flow in a production environment, but you do not want to have to change the flow depending on where you intend to run it. This is where property placeholders are useful. How to use such placeholders in your flows and how to specify their value depending on the environment is described below.
 

# Using property placeholders in flows

To use property placeholders in your eMagiz flow, follow these two simple steps:
  - place the *property placeholder support object* in your flow (if it is not there already by default): this enables property resolving for the flow and contains some settings for configuring where to look for property values (more about these settings later)
  - instead of typing the property value, use a property placeholder string (${...}): for example, the string `<${ftp.username}>` will be replaced by the value for the property with name *ftp.username*, as specified for the environment the flow is running  
  
Because the values for properties depend on the environment, the property placeholders are replaced by the actual values when starting the flow. If at this point, any property does not have a value specified, starting the flow will fail with an error like this: _Could not resolve placeholder 'ftp.username'._ For the different options to specify property values, see below.

 
Note that it is also possible to use property placeholders for just a part of a full property value. For example, you could specify the string `<http://${ws.host}:${ws.port}/ws/>` as the value for a web service URL in your flow. If property *ws.host* has the value *www.example.com* and property *ws.port* has the value *8080*, this would result in the following value for the web service URL: `<http://www.example.com:8080/ws/>`.
 
# Specifying property values

To specify values for properties, you'll need to do the following:
  - specify the property as a name/value pair
  - configure eMagiz so it knows where to look for these name/value pairs
Currently eMagiz supports four different sources for specifying custom properties: 'embedded' in your flow, in a *.properties* file, using Mendix constants, or on https://my.emagiz.com. How to perform the above two actions for each of these sources is described below.
 

# 'Embedded' properties

'Embedded' properties are properties that have their value defined in the flow that uses them. In contrast to the other property sources, this option is **not** environment specific: it is mostly useful as a fall-back source for properties that are not specified elsewhere, much like providing a set of default values that can be overridden in specific environments.

**Specifying property name/value**
Add a properties support object to your flow. Double click it and use the add entry button to add new name/value pairs.
 
**Configuring property source**
Double click the property placeholder support object in your flow and in field property ref. select the properties support object you just created.

# '.properties' file

A *.properties* file is just a text-file that specifies property values. Because it only requires a file to be present, this option works for every eMagiz runtime mode.
 
**Specifying property name/value**  

Create a text-file (the preferred file extension is *.properties*, but this is not a requirement), and add properties by typing them in this file. Each property should be on a seperate line, and the name and value should be separated by an equals sign ('='). For example:

    mendix.ws.url=http://www.example.com/ws/ExampleService/
    mendix.ws.username=myUsername
    mendix.ws.password=myPassword
    
Note that a backslash ('\') is the escape character, so for file paths you should always use forward slashes ('/'), even when running on Windows. For more information about the syntax (including the alternate XML syntax), see the Java [documentation](https://docs.oracle.com/javase/6/docs/api/java/util/Properties.html).

 
# Configuring property source

Double click the *property placeholder support object* in your flow and in field *location* (on the advanced tab-page) provide a reference to your *.properties* file. To make sure this file reference works on all environments (which is usually why you're using such a file in the first place), make sure this is a relative path. By convention you should place your *.properties* files in the *config* directory; a relative path to such a file would look something like `config/example.properties`.  

# Mendix constants as a property source

Mendix constants can also be used to specify properties. While this obviously only works when running eMagiz in a Mendix Business Server, the advantage is that you can keep all your project settings (both for your Mendix project and your eMagiz flows) in one location.
 
**Specifying property name/value**
Add a constant with the same name as your property to your Mendix project, and give it the desired value (in the Mendix Modeler, in the Mendix Service Console or in the .yaml file, depending on the environment). Note that only a limited set of characters is allowed for Mendix constants names: if your property name contains any characters that are not allowed by Mendix, just replace them with an underscore character. For example, to specify property *ftp.username*, create a Mendix constant named *ftp_username*.
 
**Configuring property source**
Because Mendix constants are set on the module level (and multiple modules can define constants with the same name), you have to specify which module(s) eMagiz should use when searching for matching constants. To specify this, provide this module name (or names) as the value for the *PropertySourceModuleNames* constant of the *EMagiz_Runtime* module in your project.
 
**'https://my.emagiz.com' as a property source (preferred)**

It is also possible to specify properties using the eMagiz portal at https://my.emagiz.com. This option works for every eMagiz runtime mode and provides users with one central location to manage the properties of all their eMagiz runtimes, but it does require a working internet connection on your deployment server.
 
**Specifying property name/value**

Go to https://my.emagiz.com and log in. Select your bus, and go to *Deploy > Properties* and use the *new, edit* and *delete* buttons to manage your properties. Note that you not only have to provide the name and value for a property, but also which container (and environment) the property is for.
 
**Configuring property source (automatically done for you already, except for Mendix)**

Specify the web service URL, username and password that should be used for retrieving properties in your eMagiz runtime. The URL should be set to `https://my.emagiz.com/ws/` and the username/password can be found in the eMagiz portal (see *Deploy > On-premises*). Specifying these settings depends on the eMagiz runtime mode:
  - **Standalone**: edit the console/run-in-console.cmd (Windows) or *console/run-in-console.sh* (Linux) file, and specify values for the options *SAAS_URL, SAAS_USERNAME* and *SAAS_PASSWORD*
  - **Windows service**: edit the *service/emagiz-service.ini* file, and specify values for the options *emagiz.saas.ws.url*, *emagiz.saas.ws.username* and *emagiz.saas.ws.password*
  - **Mendix**: specify values for the constants *SaasWsUrl*, *SaasWsUsername* and *SaasWsPassword* from the *EMagiz_Runtime* module
