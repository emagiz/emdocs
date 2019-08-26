
# Use custom Java startup arguments
https://my.emagiz.com/link/documentation/119
In every runtime you can specify additional arguments that java uses for it's virtual machine e.g. if you require a separate truststore for self signed certificates or if you have a root ca which is not included in the default java truststore.

 

## Console
In the console you can specify these by adding them to the following line.

    java -server -Xms%INITIAL_MEMORY% -Xmx%MAXIMUM_MEMORY% -XX:MaxPermSize=%MAX_PERM_SIZE% -Dfile.encoding=UTF-8 -Demagiz.ssl.mappings=%SSL_MAPPINGS_FILE% -Djavax.net.ssl.trustStore=serverTrust  -jar %LAUNCHER_JAR% license=%LICENSE_FILE% extdir=%EXTENSIONS_DIR% jvm=%JVM_NAME% saasurl=%SAAS_URL% saasusr=%SAAS_USERNAME% saaspwd=%SAAS_PASSWORD% logconf=%CUSTOM_LOGBACK_CONFIG% %CONFIG_1% %CONFIG_2%...

Be sure not to declare them after the -jar declaration.

## Windows service

In the windows service you can add them at the Java VM settings sections.

    vmarg.1=-Xrs\
    vmarg.2=-server
    vmarg.3=-XX:MaxPermSize=64M
    vmarg.4=-Xms64M
    vmarg.5=-Xmx128M
    vmarg.6=-Dfile.encoding=UTF-8
    ;vmarg.7=-Demagiz.ssl.mappings=
    ;vmarg.8=-Djavax.net.ssl.keyStore=
    ;vmarg.9=-Djavax.net.ssl.keyStorePassword=
    vmarg.10=-Djavax.net.ssl.trustStore=serverTrust
    
Ensure that the vmarg counter is not declared twice, otherwise only the last declaration will be made.

## Linux script

In the linux script you can add them to the following line in the emagiz-daemon file.

    JAVA_ARGS="-server -Xms$INITIAL_MEMORY -Xmx$MAXIMUM_MEMORY -XX:MaxPermSize=$MAX_PERM_SIZE -Dfile.encoding=UTF-8 -Demagiz.ssl.mappings=$SSL_MAPPINGS_FILE -Djavax.net.ssl.trustStore=serverTrust  -jar $LAUNCHER_FILE license=$LICENSE_FILE extdir=$EXTENSIONS_DIR jvm=$JVM_NAME saasurl=$SAAS_URL saasusr=$SAAS_USERNAME saaspwd=$SAAS_PASSWORD logconf=$CUSTOM_LOGBACK_CONFIG $CONFIG1 $CONFIG2 $CONFIG3 ... "

Ensure that the declaration is made before the -jar call.
