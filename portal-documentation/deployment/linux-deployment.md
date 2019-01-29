# Linux deployment
https://my.emagiz.com/link/documentation/9
This manual describes how to configure a linux environment for running an eMagiz runtime.

We currently support the following distributions:

 

  - Debian 6
  - Ubuntu 10 and up
  - RHEL 6
 

Other distributions especially forks of the above may be compatible but are not fully tested and supported by eMagiz.

 

To be able to run the eMagiz runtime the following dependencies are required to be installed on your system.

 

  - Java 1.7 or 1.8
 

The eMagiz runtime can be downloaded from the Saas portal.

 

We suggest installing the emagiz runtime in the /opt/eMagiz/<runtime_folder>/

 

According to FHS this is the directory to install any data required for services provided by the system.

 

This way you are able to install multiple eMagiz instances inside the /opt folder. If you were to host multiple eMagiz environments belonging to different customers you could consider adding 1 extra layer to the directory structure, namely that of the user. e.g. /opt/eMagiz/<emagizUser>/<runtime_folder/

 

## Preparing the system  

It is highly recommended to create a separate user that is allowed to run one or multiple runtimes. If one customer has multiple JVM's it is allowed to use the same user for each JVM, however when you have a multiple runtimes belonging to a different customer you should separate these and make 1 user for each of these groups.

    admin@community:~$ sudo adduser --no-create-home --gecos "Emagiz test user,,," emagiztest
    Adding new group `emagiztest' (GID 123) ...
    Adding new user `emagiztest' (UID 116) with group `emagiztest' ...
    Not creating home directory `/home/emagiztest'.
    admin@community:~$    

When the user is created add the directory structure and copy the emagiz runtime to that directory. Afterwards set the correct user rights.

    admin@community:~$ sudo mkdir -p /opt/emagiz/emagiztest
    admin@community:~$ sudo cp ./emagiz-3.8.0-standalone.zip /opt/emagiz/emagiztest/
    admin@community:~$ cd /opt/emagiz/emagiztest/
    admin@community:/opt/emagiz/emagiztest$ sudo unzip emagiz-3.8.0-standalone.zip
    admin@community:/opt/emagiz/emagiztest$ sudo rm -r emagiz-3.8.0-standalone.zip
    admin@community:/opt/emagiz/emagiztest$ sudo chown emagiztest:emagiztest * -R
    admin@community:/opt/emagiz/emagiztest$ sudo chmod 770 config/ console/ extensions/ libraries/ logs/ resources/ service/
    admin@community:/opt/emagiz/emagiztest$ ls -l
    total 40
    drwxrwx--- 2 emagiztest emagiztest  4096 Mar 12 15:20 config
    drwxrwx--- 2 emagiztest emagiztest  4096 Mar 12 15:20 console
    drwxrwx--- 2 emagiztest emagiztest  4096 Mar 12 15:20 extensions
    drwxrwx--- 2 emagiztest emagiztest 16384 Mar 12 15:21 libraries
    drwxrwx--- 2 emagiztest emagiztest  4096 Mar 12 15:20 logs
    drwxrwx--- 2 emagiztest emagiztest  4096 Mar 12 15:20 resources
    drwxrwx--- 2 emagiztest emagiztest  4096 Mar 12 15:20 service
    admin@community:/opt/emagiz/emagiztest$
    
Now you can configure the emagiz process by filling in the appropriate configuration settings under service/emagiz-daemon.

Next you should pick the appropriate startup script and rename it so no more spaces exists in its name.

    admin@community:/opt/emagiz/emagiztest$ cd service/
    admin@community:/opt/emagiz/emagiztest/service$ mv "daemon-installer (Debian).sh" daemon-installer.sh
    admin@community:/opt/emagiz/emagiztest/service$ sudo chmod +x daemon-installer.sh emagiz-daemon  
    
Then you should edit this script and fill in all the configuration settings.

| Properties | Description |
| :--- | :---|
| NAME | Name of the daemon that is used to register the daemon as a service. This name should be unique for each instance of emagiz you wish to run. |
| SERVICE | A description of the service used in the log files and as feedback to describe the service. |
| DAEMON | Path to the daemon in the example case this would be /opt/emagiz/emagiztest/service/emagiz-daemon | 
| SERVICELOGFILE | Path to the service log file in the example case this would be /opt/emagiz/emagiztest/logs/service.log |
| USER | User that is going to run the emagiz process. e.g. emagiztest |
| GROUP | Group that is allowed to start the process. e.g. emagiztest | 

After filling the appropriate settings you can test the script by running it. Make sure you have the license file in place otherwise you will not be able to start your process.
 
admin@community:/opt/emagiz/emagiztest/service$ sudo ./daemon-installer.sh start
When the service starts succesfully, you can call the same command again except with the stop command to stop the daemon.
Now all that remains is to install the daemon as a service you can do this by calling the command.

    admin@community:/opt/emagiz/emagiztest/service$ sudo ./daemon-installer.sh install

From now on you can start and stop the service by calling the service <servicename> start/stop
 
    admin@community:/opt/emagiz/emagiztest/service$ sudo service emagizService start
 
 Or
 
    admin@community:/opt/emagiz/emagiztest/service$ sudo initctl emagizService start
