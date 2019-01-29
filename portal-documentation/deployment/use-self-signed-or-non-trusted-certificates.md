## Using self signed or non-trusted certificates

https://my.emagiz.com/link/documentation/120  
Sometimes when connecting to another application it publishes a self-signed or non trusted certificate. To recognize what type of certificate you are dealing with you can open it in your browser if this marks the certificate as not trusted then java is unlikely to accept it as a trusted certificate. Some root certificates however are not (yet) registered by java which means that for these you will have to add that root certificate either to the default java trust store or create your own default trust store.

 

If you encouter the following error you are dealing with a non-trusted certificate:

 

PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

 

## Trusting certificates
Each time a self-signed certificate is published or a non-trusted certificated you are required to put them either into the default java truststore or to create your own truststore. To create or modify a Java trust (key) store: I recommend using the open source tool Portecle for creating and modifying Java trust store files.

 
## Add to the default trust store
To add the non-trusted certificates to the default trust store you can open use Portecle to Open CA Certs Keystore. The default password for this keystore is changeit. 

 

## Create trust store*
To create a trust store i would recommend to first make a copy of the cacerts file located in the path/to/javaruntime/jre/lib/security/cacerts. The default password of the cacerts file is changeit. You can also use Portecle to change the password of this trust store.

 

Once you've got your Java trust store file, you have to configure JSSE to use it. You do this by adding two system properties to Java: one specifying the location of the trust store file (named javax.net.ssl.trustStore), and one specifying the password for that trust store (named javax.net.ssl.trustStorePassword). You can do this by adding the following to the Java startup arguments:

    -Djavax.net.ssl.trustStore=path/to/myTruststore.jks -Djavax.net.ssl.trustStorePassword=myPassword

## Adding certificate to trust store

Now that we have a trust store we can add our (self signed) certificates to it. Import the root certificate of the required certificate this allows you to call any certificate created by this ca.

 

*Note that if your java virtual machine also has a hornetq connector that use a trust store that this trust store will be overwritten by the custom trust store. This means that you will have to add the trusted certificates from the hornetq connector trust store to the newly created trust store.
