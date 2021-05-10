## 1. CONTEXT AND REQUIREMENTS   
This document explains how to create a Java trust- and keystore to be used in the eMagiz Create phase. In this document 3 different scenarios are worked out to install and update certificates


- Keystore and Truststore inside the eMagiz flow (support object *SSL web service message sender used by the Web Service outbound gateway*)
- Keystore and Truststore inside the web service hosted in the eMagiz Cloud
- Keystore and Truststore inside on-premise Connectors

In other scenarios please consult an eMagiz consultant local to your region. 


## 2.	BEST PRACTICES
- When you have different certificates for test, acceptance or production, you should use a property for the trust- and key store path in your SSL web service message sender component. So that you may use the right keystore for each environment. 
- Save the passwords you set for the keystores in a KeePass password file (or similar tools) so you have a backup for the key store passwords in case someone changes or deletes your properties.
- Save the certificates in an client internal support application so you can set a notification for when the certificate is about to expire.



## 3.	HOW-TO STEPS FOR KEYSTORE IN EMAGIZ FLOWS
Starting point of this part is that you have already received a certificate file (.pfx, .abc, etc.). Please obtain this before proceeding to the next step. Follow these steps carefully in order to acquire the desired result. Before you head into the how-to steps make sure you have downloaded the program Keystore Explorer from the internet. We will use this program to create our trust- and keystore.

***How to create the proper certificate file (.CER)***

1. Open keystore Explorer
2. Browse to the PFX or ABC file on your machine and open it
3. Apply the password in order to open it
4. Right click on the key, select View Details, Certificate Chain Details. 
5. Select the top level in the certificate Chain and press Export
6. Export settings: select the X.509 option
7. Select folder where to store the .cer file

***How to create the P12 file containing the keypair***

1. Open keystore Explorer
2. Browse to the PFX or ABC file on your machine and open it
3. Apply the password in order to open it
4. Right click on the key, and select Export Keypair
5. Enter the password of the PFX or ABC file
6. Enter the new password for the keypair you are going to export
7. Save the file locally on your disk as a .p12 file

8. Open the .p12 file and using the password just created
9. Right click on the key, select Edit Certificate Chain, and then Remove Certificate (it will remove the top level certificate of the certificate chain)
10. Save file


***How to create a Java Trust Store – containing your trusted certificate(s)***

1.	Open Keystore Explorer.
2.	Select Create a new keystore (Truststores in this context are just keystores that have trusted certificates).
3.	Select JKS (Java Key Store) and press OK.
4.	Click the Import Trusted Certificate button as can be seen below.

<p align="center"><img  src="../../img/howto/keystores-section3-1.png"></p>

5.	Select the concerning certificate (.cer file).
6.	Save the file and secure it with an appropriate password that matches the password of the keystore (step 7)
7.	Give the keystore file an appropriate password.
8.	Save the keystore file with an appropriate name as an .jks file. Ensure to use something to recognize this is a trust store file

You have now created a key store file containing the trust store.

***How to create a java keystore – containing your keypair***

1.	Open Keystore Explorer.
2.	Select Create a new key store file.
3.	Select JKS (Java Key Store) and press OK.
4.	Click the Import Key Pair as can be seen below.

<p align="center"><img  src="../../img/howto/keystores-section3-2.png"></p>

5.	Select PKCS #12 (assuming you received a .p12 file)
6.	Type in the Decryption Password and select the .p12 file 
7.	Save the file and secure it with an appropriate password that matches the password of the keystore (step 7)
8.	Give the keystore file an appropriate password.
9.	Save the keystore file with an appropriate name as an .jks file. Ensure to use something to recognize this is a key store file

***How to use a SSL web service message sender in your eMagiz flow to set-up a Two-Way SSL Authentication: Same key- and truststore for all environments***

1.	Open your flow and start editing.
2.	Create your web service outbound gateway if you have not done that already.
3.	Upload the key- and truststore in the Resources tab.
4.	Create your SSL web service message sender.
	- in case you update this object, please validate in the Advanced tab if the Certificate Alias is used. Select the proper value
5.	Select your key- and truststore in the key- and truststore paths.
6.	Create your key- and truststore password properties and type them in the appropriate fields.

<p align="center"><img  src="../../img/howto/keystores-section3-3.png"></p>

7.	Open your web service outbound gateway, go to the advanced tab and select your SSL web service message sender in the Message sender field.

***How to use a SSL web service message sender in your eMagiz flow to set-up a Two-Way SSL Authentication: Different key- and truststores for every environment***

1.	Open your flow and start editing.
2.	Create your web service outbound gateway if you have not done that already.
3.	Upload all the key- and truststores in the Resources tab (in this case we have different key- and truststores for acceptance and production).

<p align="center"><img  src="../../img/howto/keystores-section3-4.png"></p>

4.	Now download all your key- and truststores to know what their paths will be.

<p align="center"><img  src="../../img/howto/keystores-section3-5.png"></p>

5.	For each environment create a key- and trustore property containing the path to your key- and truststore. The value should be: “resources/[filename of the key- or truststore]”. So in the case of the acceptance keystore this would be:
“resources/00-103915_emagiz_esb_a19_keystore.jks”
<p align="center"><img  src="../../img/howto/keystores-section3-6.png"></p>

6.	Create your SSL web service message sender.
7.	Type in your key- and truststore path properties.
	- in case you update this object, please validate in the Advanced tab if the Certificate Alias is used. Select the proper value
8.	Create your key- and truststore password properties and type them in the appropriate fields.

<p align="center"><img  src="../../img/howto/keystores-section3-7.png"></p>

9.	Open your web service outbound gateway, go to the advanced tab and select your SSL web service message sender in the Message sender field.

## 4. HOW-TO STEPS FOR CERTIFICATES IN EMAGIZ CLOUD
 
These how to steps are valid for both updates and for new certificates for web services hosted in eMagiz. 

Key Assumptions:
- Webservice for which the certificate is meant, is already created and is successfully deployed in the environment for which the certificate is to be updated 
- Routes in the Deploy Architecture have been configured for this specific web service
- eMagiz Support will deploy the actual certificate in the eMagiz Cloud - focus here is to ensure the linkage between that certificate and the eMagiz platform instance

1. In order to use the certificate for the web service, it needs to be signed by eMagiz. Please contact your eMagiz Partner to obtain such a certificate. Ensure to have a Common Name for the Certificate as a reference
2. Log on to the eMagiz Portal
3. Open the eMagiz platform instance
4. Go to the Deploy fase ad choose the right environment (TAP)
5. Open Architecture section
6. Right click in the whitespace and select Certificates
7. Click on New and enter the Common Name and a Client Name - click Save
8. Remove the popup screen and right the white space to select Routes.
9. Open the route of the webservice for which the certificate is to be set
10. Upload the certificate via Certificate click Save.
11. Click apply to environment bottom left in the Architecture page.


## 5. HOW-TO STEPS FOR ON-PREMISE CONNECTOR LEVEL CERTIFICATES

Please ensure to shut down the eMagiz Connector before proceeding.

1. Open the folder location where the eMagiz is installed
2. Open the resources folder and put the keystore & truststore you would like to use
3. Open the etc folder and open the wrapper.config file
4. Add additionele wrapper.java regels as listed below

	- wrapper.java.additional.15=-Djavax.net.ssl.keyStore=
	- wrapper.java.additional.16=-Djavax.net.ssl.keyStorePassword=
	- wrapper.java.additional.17=-Djavax.net.ssl.trustStore=
	- wrapper.java.additional.18=-Djavax.net.ssl.trustStorePassword=
	- wrapper.java.additional.18=-Demagiz.ssl.mappings=

5. Enter the proper values, for example:

	- wrapper.java.additional.15=-Djavax.net.ssl.keyStore=resources/test-keystore.jks
	- wrapper.java.additional.16=-Djavax.net.ssl.keyStorePassword=GoedWachtwoord1!
	- wrapper.java.additional.17=-Djavax.net.ssl.trustStore=resources/test-truststore.jks
	- wrapper.java.additional.18=-Djavax.net.ssl.trustStorePassword=GoodPassword1!
	- wrapper.java.additional.18=-Demagiz.ssl.mappings=resources/sslconfig.properties

