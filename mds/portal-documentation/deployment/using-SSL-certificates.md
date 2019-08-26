# Using SSL (client) certificates
https://my.emagiz.com/link/documentation/7
Sometimes when connecting to another application (usually using an HTTPS connection), it is required to have an SSL or TLS client certificate installed on your system for authentication purposes. In eMagiz (just like most Java applications) this is handled by the Java Secure Socket Extension (JSSE), which is a security component that is part of the Java SE 6 platform. For more information about JSSE, see the official JSSE reference guide.

How you should configure JSSE depends on the Java runtime you are using: the examples in this chapter all assume you are running on the recommended Sun (now Oracle) Java SE 6 runtime. If you are using another Java runtime, please refer to that vendor's documentation.

 

## Registering your own SSL (client) certificates
Each time a certificate is required, for example when setting up an HTTPS connection for a web service, JSSE will look at all registered certificates to find a suitable candidate. These certificates are stored in a so-called key store: basically this is an encrypted archive file containing all your certificates, protected by a password.

 

The first step to register your own SSL (client) certificates is to put them all into a single Java key store: I recommend using the open source tool Portecle for creating and modifying Java key store files (.jks). Note that when creating a key store, you'll have the option to put a password on the key store itself and on individual entries: make sure you use the same password for both levels of security, otherwise JSSE won't be able to access the information!

Once you've got your Java key store file (.jks), you have to configure JSSE to use it. You do this by adding two system properties to Java: one specifying the location of the key store file (named javax.net.ssl.keyStore), and one specifying the password for that key store (named javax.net.ssl.keyStorePassword). You can do this by adding the following to the Java startup arguments:

    -Djavax.net.ssl.keyStore=path/to/myKeystore.jks -Djavax.net.ssl.keyStorePassword=myPassword
    
## Using multiple SSL client certificates for connecting to different hosts
The default JSSE implementation that ships with the Java runtime selects certificates from the key store based on some attributes of the requested certificate (e.g. the type of encryption algorithm used, the issuer of the certificate, etc). If there are multiple certificates with these same attributes, the first one is used. This approach works fine when connecting to a single SSL service, but can give problems when connecting to multiple SSL services that each require their own certificate. For these scenarios, eMagiz provides an alternative JSSE key manager implementation that extends the default behaviour by giving the user the option to specify which certificate to use for individual servers.

 

Because this is an extension of the default JSSE implementation, you should first follow the steps mentioned above for registering your own SSL (client) certificates (i.e.: put all your certificates into one key store and configure JSSE to use this key store for locating certificates).

 

Next you have to specify which certificates to use for what SSL connections. You do this by creating a mapping between host names of servers you want to connect to and the names of the certificates to use. This mapping should be stored as a .properties file, for example:

    app1.company-a.com=certificate1
    app2.company-a.com=certificate2
    webservices.company-b.com=certificate3
    webservices.company-c.com=  
    
The host names in this file should be an exact match with the host name used for establishing the connection. If a host name is present in the mapping file but doesn't specify a certificate ("Company C" in the example), no SSL client certificate is used for connecting to it. If a host name is not found in the mapping file, the default JSSE behaviour is applied.

The certificate names in this file should be an exact match to the alias of the certificate in the key store file. You can specify these names yourself when creating the key store.

 

Lastly, JSSE needs to be configured to use the eMagiz JSSE extension based on your mapping file. This is done by specifying the name of your mapping file as the Java system property emagiz.ssl.mappings (this is in addition to the system properties javax.net.ssl.keyStore and javax.net.ssl.keyStorePassword). Add the following to the Java startup arguments:

    -Demagiz.ssl.mappings=path/to/mySslMappings.properties
