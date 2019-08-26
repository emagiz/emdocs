---
id: edit-transport-configuration
title: Edit transport configuration
sidebar_label: Edit transport configuration
---
#### Sort order
The order in which the JMS servers will be tried when creating the initial connection. Once a connection is made, the cluster topology is downloaded and is used instead.

For example, the backup server should have a higher number than the live server so the live server will be tried first.

<i>Required</i>

#### Name
Name uniquely identifying this transport configuration.

<i>Required</i>

#### Host
The host name or IP address to connect to.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

Default is <i>localhost</i>.

<i>Optional</i>

#### Port
The port to connect to.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

Default is <i>5445</i>.

<i>Optional</i>

#### SSL enabled
Whether or not connections created with this transport configuration should be secured with SSL/TLS.

This connection setting must match the acceptor setting on the JMS server.

#### Key store path
The path to the SSL key store which holds the client certificates.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

Note that if provided, the <code>javax.net.ssl.keyStore</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

#### Key store password
The password for the client certificate key store.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

Note that if provided, the <code>javax.net.ssl.keyStorePassword</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

#### Trust store path
The path to the trusted server certificate store.

If the server uses a self-signed certificate, you'll need to create a trust store containing this certificate. If the server uses a certificate signed by an official authority, it will most likely work without specifying a trust store because the default Java truststore already contains the recognized Certificate Authorities.

Note that if provided, the <code>javax.net.ssl.trustStore</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

#### Trust store password
The password to the trusted server certificate store.

Note that if provided, the <code>javax.net.ssl.trustStorePassword</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

#### Sort order
The order in which the JMS servers will be tried when creating the initial connection. Once a connection is made, the cluster topology is downloaded and is used instead.

For example, the backup server should have a higher number than the live server so the live server will be tried first.

<i>Required</i>

#### Name
Name uniquely identifying this transport configuration.

<i>Required</i>

#### Host
The host name or IP address to connect to.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

Default is <i>localhost</i>.

<i>Optional</i>

#### Port
The port to connect to.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

Default is <i>5445</i>.

<i>Optional</i>

#### SSL enabled
Whether or not connections created with this transport configuration should be secured with SSL/TLS.

This connection setting must match the acceptor setting on the JMS server.

#### Key store path
The path to the SSL key store which holds the client certificates.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

Note that if provided, the <code>javax.net.ssl.keyStore</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

#### Key store password
The password for the client certificate key store.

This is only relevant if you are using 2-way SSL (i.e. mutual authentication).

Note that if provided, the <code>javax.net.ssl.keyStorePassword</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

#### Trust store path
The path to the trusted server certificate store.

If the server uses a self-signed certificate, you'll need to create a trust store containing this certificate. If the server uses a certificate signed by an official authority, it will most likely work without specifying a trust store because the default Java truststore already contains the recognized Certificate Authorities.

Note that if provided, the <code>javax.net.ssl.trustStore</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

#### Trust store password
The password to the trusted server certificate store.

Note that if provided, the <code>javax.net.ssl.trustStorePassword</code> Java system property takes precendence over this setting.

Using a property placeholder is recommended, as connection settings usually differ between test, acceptation and production environments.

<i>Optional</i>

