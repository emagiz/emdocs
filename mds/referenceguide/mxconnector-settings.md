---
id: mxconnector-settings
title: MxConnector settings
sidebar_label: MxConnector settings
---
#### XML schema
XML schema used by the request handler to validate all incoming SOAP web service requests against. Invalid SOAP requests will result in a <i>SOAP Fault</i> response containing the validation errors.

This XML schema is also used to automatically create the WSDL from, placing the following requirements on the contents:
- the XML schema must specify a "targetNamespace"
- for each web service operation (i.e. for every entry connector flow) there must be a request & response pair specified
- the name of a request element must be the operation name appended with the suffix "Request"
- the name of a response element must be the operation name appended with the suffix "Response"
- the response elements of all asynchronous entry connector flows must be empty

<i>Required</i>

#### Username
Username for accessing the web services hosted by this request handler (HTTP basic access authentication).

When deploying your Mendix app in the Mendix cloud it's not possible to prevent public access to this request handler, so using (random) credentials that are impossible to guess is strongly recommended.

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Required</i>

#### Password
Password for accessing the web services hosted by this request handler (HTTP basic access authentication).

When deploying your Mendix app in the Mendix cloud it's not possible to prevent public access to this request handler, so using (random) credentials that are impossible to guess is strongly recommended.

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Required</i>

#### Failover
Determines whether or not the connection to the JMS server should support failover.

Enabling failover for the connection is only useful when there are at least two JMS servers: one live server and one backup server.

#### Cluster
Determines whether or not the connection to the JMS server should support clusters, i.e. the JMS client may connect to any available JMS server in the cluster.

Enabling cluster connections is only useful when there is a cluster of at least two JMS servers available that this connector could create connections with.

#### Username
Username for creating connections with the JMS server(s).

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Optional</i> ; security can be disabled on the JMS server, but this is not recommended.

#### Password
Password for creating connections with the JMS server(s).

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Optional</i> ; security can be disabled on the JMS server, but this is not recommended.

#### Sync receive timeout
Timeout for the JMS message consumer to receive the JMS reply message in case of <b>synchronous</b> (request/response) message flows.

Default is <code>20000</code> milliseconds (twenty seconds).

<i>Optional</i>

#### Queue
Name of the JMS queue this exit connector will consume messages from.

<i>Required</i>

#### XML to domain mapping
Name of the Mendix XML-to-domain mapping to execute on the message payload (must include the module name).

Example: <code>MyModule.MyXmlToDomainMapping</code>

<i>Required</i>

#### Transaction
Whether to execute the Mendix XML-to-domain mapping in a (Mendix) transaction or not.

Not using a transaction might have a positive impact on the performance, but could lead to an "incorrect" database state (without a transaction, no rollback is performed when errors occur during the XML import).

Default is <i>false</i>.

#### Logout
The Mendix XML-to-domain mapping is executed in a newly created system context each time a message arrives. Due to changes in the garbage collection from Mendix 4.8.0 onwards, you might get out-of-memory exceptions when working with high volumes of messages. In this case "logging out" the system session solves this because it will immediately trigger the garbage collection. In Mendix 5 however, this is no longer an option.

To conclude: when running in Mendix 4.7.2 or lower, or any Mendix 5 version, you'll want to disable this option. In any Mendix 4 version from 4.8.0 onwards, you <i>might</i> need to enable it.

Default is <i>false</i>.

#### Queue
Name of the JMS queue this exit connector will consume messages from.

<i>Required</i>

#### Queue
Name of the JMS queue this entry connector will send its messages to.

<i>Required</i>

#### Request qualified name
Fully qualified name of the web service request XML root element. The definition of this XML element must be specified in the XML schema of the request handler.

Usually consists of the web service namespace, the web service operation, and the suffix 'Request'. For example: <code>{http://www.example.com/}SendMessageRequest</code>

<i>Required</i>

#### Queue
Name of the JMS queue this entry connector will send its request messages to.

<i>Required</i>

#### Response queue
Name of the JMS queue this entry connector will consume the response messages from.

<i>Required</i>

#### Request qualified name
Fully qualified name of the web service request XML root element. The definition of this XML element must be specified in the XML schema of the request handler.

Usually consists of the web service namespace, the web service operation, and the suffix 'Request'. For example: <code>{http://www.example.com/}SendMessageRequest</code>

<i>Required</i>

#### Queue
Name of the JMS queue this exit connector will consume request messages from.

<i>Required</i>

#### Response queue
Name of the JMS queue this exit connector will send its response messages to.

<i>Required</i>

#### Webservice URL
URL of the Mendix web service where this exit connector should deliver its messages to.

Note that when running in the Mendix cloud, the only option is to use the public URL. For example: <code>https://myapp.mendixcloud.com/ws/MyService</code>

Using a property placeholder is recommended, as the URL usually differs between test, acceptation and production environments.

<i>Required</i>

#### Mx username
Username for accessing the web service hosted by the Mendix app.

When deploying your Mendix app in the Mendix cloud it's not possible to prevent public access to the web services, so using (random) credentials that are impossible to guess is strongly recommended.

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Optional</i> ; security can be disabled on Mendix web services, but this is not recommended when the app is publicly accessible.

#### Mx password
Password for accessing the web service hosted by the Mendix app.

When deploying your Mendix app in the Mendix cloud it's not possible to prevent public access to the web services, so using (random) credentials that are impossible to guess is strongly recommended.

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Optional</i> ; security can be disabled on Mendix web services, but this is not recommended when the app is publicly accessible.

#### Connect timeout
Sets a specified timeout value, in milliseconds, to be used when opening a communications link to the Mendix web service. If the timeout expires before the connection can be established, a <code>java.net.SocketTimeoutException</code> is raised. A timeout of zero is interpreted as an infinite timeout.

<i>Optional</i> ; if not specified the Java default of <code>0</code> (infinite) is used.

#### Read timeout
Sets the read timeout to a specified timeout, in milliseconds. A non-zero value specifies the timeout when reading (response) data after successfully connecting to the Mendix web service. If the timeout expires before there is data available for read, a <code>java.net.SocketTimeoutException</code> is raised. A timeout of zero is interpreted as an infinite timeout.

Note that this is a client-side setting: after a timeout the eMagiz Mendix Connector will execute the configured error handling, but Mendix might actually still be busy processing the request. This can lead to data duplication or even thread starvation in Mendix, so consider each use case carefully.

<i>Optional</i> ; if not specified the Java default of <code>0</code> (infinite) is used.

#### Webservice URL
URL of the Mendix web service where this exit connector should deliver its messages to.

Note that when running in the Mendix cloud, the only option is to use the public URL. For example: <code>https://myapp.mendixcloud.com/ws/MyService</code>

Using a property placeholder is recommended, as the URL usually differs between test, acceptation and production environments.

<i>Required</i>

#### Mx username
Username for accessing the web service hosted by the Mendix app.

When deploying your Mendix app in the Mendix cloud it's not possible to prevent public access to the web services, so using (random) credentials that are impossible to guess is strongly recommended.

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Optional</i> ; security can be disabled on Mendix web services, but this is not recommended when the app is publicly accessible.

#### Mx password
Password for accessing the web service hosted by the Mendix app.

When deploying your Mendix app in the Mendix cloud it's not possible to prevent public access to the web services, so using (random) credentials that are impossible to guess is strongly recommended.

Using a property placeholder is recommended, as the credentials usually differ between test, acceptation and production environments.

<i>Optional</i> ; security can be disabled on Mendix web services, but this is not recommended when the app is publicly accessible.

#### Connect timeout
Sets a specified timeout value, in milliseconds, to be used when opening a communications link to the Mendix web service. If the timeout expires before the connection can be established, a <code>java.net.SocketTimeoutException</code> is raised. A timeout of zero is interpreted as an infinite timeout.

<i>Optional</i> ; if not specified the Java default of <code>0</code> (infinite) is used.

#### Read timeout
Sets the read timeout to a specified timeout, in milliseconds. A non-zero value specifies the timeout when reading (response) data after successfully connecting to the Mendix web service. If the timeout expires before there is data available for read, a <code>java.net.SocketTimeoutException</code> is raised. A timeout of zero is interpreted as an infinite timeout.

Note that this is a client-side setting: after a timeout the eMagiz Mendix Connector will execute the configured error handling, but Mendix might actually still be busy processing the request. This can lead to data duplication or even thread starvation in Mendix, so consider each use case carefully.

<i>Optional</i> ; if not specified the Java default of <code>0</code> (infinite) is used.

### 
Determines whether or not the connection to the AMQP server should support failover. 

Enabling failover for the connection is only useful when there are at least two JMS servers: one live server and one backup server.

### 
Determines whether or not the connection to the AMQP server should support clusters, i.e. the JMS client may connect to any available JMS server in the cluster.

Enabling cluster connections is only useful when there is a cluster of at least two JMS servers available that this connector could create connections with.

### 
Username value used to authenticate the connection.

<i>Required</i>

### 
The password value used to authenticate the connection.

<i>Required</i>

### 
Whether to verify that the hostname being connected to matches with the provided server certificate.

Default is true.

### 
Enable the WebSocket protocol.

Default is true.

### 
This is the path to the SSL key store on the client which holds the client certificates. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.keyStore".

### 
This is the password for the SSL key store on the client which holds the client certificates. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.keyStorePassword"

### 
This is the path to the trusted client certificate store on the server. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.trustStore".

### 
This is the password to the trusted client certificate store on the server. Only used when SSL is enabled.

Default is to read from the system property "javax.net.ssl.trustStorePassword"

### 
Enable SSL to secure connections.

Default is false.

#### Error queue
The name of the JMS queue (hosted by the JMS server of this message bus) where this connector will send any error messages to.

Error messages are generated when an exit connector flow cannot successfully deliver a message to the Mendix app and that flow's error handling is set to <i>error message</i> (the default).

<i>Required</i>


The name of the header to be added to every outgoing message, to identify which tenant sent it.

Default: <i>busName</i>_sourceTenant

<i>Required</i>


The name of the tenant to be added to every outgoing message, to identify which tenant sent it.

Default (property): ${<i>systemName</i>.tenant.name}

<i>Required</i>

#### XML schema
XML schema to validate messages against after consuming them from the JMS queue but before delivering them to the Mendix app. If validation fails the error handling of this exit connector is triggered.

<i>Optional</i> ; if not specified, no validation is performed on the messages.

#### Error handling
How this exit connector should handle errors when delivering a message to the Mendix app fails:

<b>Error message</b>
Sends an error message (containing the cause and the message content) to the error queue on the JMS server and commits the JMS transaction.

<b>Ignore</b>
Silently ignores the error and commits the JMS transaction. Note that in this case the message content is lost.

<b>Log</b>
Sends the error to the Mendix log and commits the JMS transaction. Note that in this case the message content is lost.

<b>Rollback</b>
Rolls back the JMS transaction. What happens next with the message depends on the redelivery settings of the JMS queue this exit connector consumed the message from.

Default is <i>error message</i>.

#### Maximum attempts
The number of attempts before a retry becomes impossible. The number of attempts includes the initial try.

Default is <code>1</code>: only try once.

#### Back off period
The back off period in milliseconds. This is a fixed period of time before the next attempt is made.

If the maximum number of attmpts is set to 1 (default), this setting has no effect.

Default is <code>1000</code> ms (1 second).

#### Concurrent consumers
Configure the concurrency behaviour of this exit connector, by specifing the initial number of concurrent consumers to create, the maximum number of concurrent consumers that is allowed to be created and the idle consumer limit:

<b>Initial concurrent consumers</b>
Specifying a higher value for this setting will increase the standard level of scheduled concurrent consumers at runtime: this is effectively the minimum number of concurrent consumers which will be scheduled at any given time. This is a static setting; for dynamic scaling, consider specifying the <i>maximum concurrent consumers</i> setting instead.

<b>Maximum concurrent consumers</b>
If this setting is higher than <i>initial concurrent consumers</i>, the listener container will dynamically schedule new consumers at runtime, provided that enough incoming messages are encountered. Once the load goes down again, the number of consumers will be reduced to the standard level again. Raising the number of concurrent consumers is recommendable in order to scale the consumption of messages coming in from a queue. However, note that any ordering guarantees are lost once multiple consumers are registered. In general, stick with 1 consumer for low-volume queues.

<b>Idle consumer limit</b>
Specifies the limit for the number of consumers that are allowed to be idle at any given time. This limit is used to determine if a new invoker should be created. Increasing the limit causes invokers to be created more aggressively. This can be useful to ramp up the number of invokers faster. The default is <code>1</code>, only scheduling a new invoker (which is likely to be idle initially) if none of the existing invokers is currently idle.

Default for all three settings is <code>1</code>.

<i>Optional</i>

#### XML schema
XML schema to validate messages against after consuming them from the JMS queue but before delivering them to the Mendix app. If validation fails the error handling of this exit connector is triggered.

<i>Optional</i> ; if not specified, no validation is performed on the messages.

#### Error handling
How this exit connector should handle errors when delivering a message to the Mendix app fails:

<b>Error message</b>
Sends an error message (containing the cause and the message content) to the error queue on the JMS server and commits the JMS transaction.

<b>Ignore</b>
Silently ignores the error and commits the JMS transaction. Note that in this case the message content is lost.

<b>Log</b>
Sends the error to the Mendix log and commits the JMS transaction. Note that in this case the message content is lost.

<b>Rollback</b>
Rolls back the JMS transaction. What happens next with the message depends on the redelivery settings of the JMS queue this exit connector consumed the message from.

Default is <i>error message</i>.

#### Maximum attempts
The number of attempts before a retry becomes impossible. The number of attempts includes the initial try.

Default is <code>1</code>: only try once.

#### Back off period
The back off period in milliseconds. This is a fixed period of time before the next attempt is made.

If the maximum number of attmpts is set to 1 (default), this setting has no effect.

Default is <code>1000</code> ms (1 second).

#### Concurrent consumers
Configure the concurrency behaviour of this exit connector, by specifing the initial number of concurrent consumers to create, the maximum number of concurrent consumers that is allowed to be created and the idle consumer limit:

<b>Initial concurrent consumers</b>
Specifying a higher value for this setting will increase the standard level of scheduled concurrent consumers at runtime: this is effectively the minimum number of concurrent consumers which will be scheduled at any given time. This is a static setting; for dynamic scaling, consider specifying the <i>maximum concurrent consumers</i> setting instead.

<b>Maximum concurrent consumers</b>
If this setting is higher than <i>initial concurrent consumers</i>, the listener container will dynamically schedule new consumers at runtime, provided that enough incoming messages are encountered. Once the load goes down again, the number of consumers will be reduced to the standard level again. Raising the number of concurrent consumers is recommendable in order to scale the consumption of messages coming in from a queue. However, note that any ordering guarantees are lost once multiple consumers are registered. In general, stick with 1 consumer for low-volume queues.

<b>Idle consumer limit</b>
Specifies the limit for the number of consumers that are allowed to be idle at any given time. This limit is used to determine if a new invoker should be created. Increasing the limit causes invokers to be created more aggressively. This can be useful to ramp up the number of invokers faster. The default is <code>1</code>, only scheduling a new invoker (which is likely to be idle initially) if none of the existing invokers is currently idle.

Default for all three settings is <code>1</code>.

<i>Optional</i>

#### XML schema
XML schema to validate messages against after consuming them from the JMS queue but before delivering them to the Mendix app. If validation fails the error handling of this exit connector is triggered.

<i>Optional</i> ; if not specified, no validation is performed on the messages.

#### Error handling
How this exit connector should handle errors when delivering a message to the Mendix app fails:

<b>Error message</b>
Sends an error message (containing the cause and the message content) to the error queue on the JMS server and commits the JMS transaction.

<b>Ignore</b>
Silently ignores the error and commits the JMS transaction. Note that in this case the message content is lost.

<b>Log</b>
Sends the error to the Mendix log and commits the JMS transaction. Note that in this case the message content is lost.

<b>Rollback</b>
Rolls back the JMS transaction. What happens next with the message depends on the redelivery settings of the JMS queue this exit connector consumed the message from.

Default is <i>error message</i>.

#### Maximum attempts
The number of attempts before a retry becomes impossible. The number of attempts includes the initial try.

Default is <code>1</code>: only try once.

#### Back off period
The back off period in milliseconds. This is a fixed period of time before the next attempt is made.

If the maximum number of attmpts is set to 1 (default), this setting has no effect.

Default is <code>1000</code> ms (1 second).

#### Concurrent consumers
Configure the concurrency behaviour of this exit connector, by specifing the initial number of concurrent consumers to create, the maximum number of concurrent consumers that is allowed to be created and the idle consumer limit:

<b>Initial concurrent consumers</b>
Specifying a higher value for this setting will increase the standard level of scheduled concurrent consumers at runtime: this is effectively the minimum number of concurrent consumers which will be scheduled at any given time. This is a static setting; for dynamic scaling, consider specifying the <i>maximum concurrent consumers</i> setting instead.

<b>Maximum concurrent consumers</b>
If this setting is higher than <i>initial concurrent consumers</i>, the listener container will dynamically schedule new consumers at runtime, provided that enough incoming messages are encountered. Once the load goes down again, the number of consumers will be reduced to the standard level again. Raising the number of concurrent consumers is recommendable in order to scale the consumption of messages coming in from a queue. However, note that any ordering guarantees are lost once multiple consumers are registered. In general, stick with 1 consumer for low-volume queues.

<b>Idle consumer limit</b>
Specifies the limit for the number of consumers that are allowed to be idle at any given time. This limit is used to determine if a new invoker should be created. Increasing the limit causes invokers to be created more aggressively. This can be useful to ramp up the number of invokers faster. The default is <code>1</code>, only scheduling a new invoker (which is likely to be idle initially) if none of the existing invokers is currently idle.

Default for all three settings is <code>1</code>.

<i>Optional</i>

### 
The name of the JMS queue (hosted by the JMS server of this message bus) where this connector will send any error messages to.

Error messages are generated when an exit connector flow cannot successfully deliver a message to the Mendix app and that flow's error handling is set to <i>error message</i> (the default).

### 
The name of the header to be added to every outgoing message, to identify which tenant sent it.

Default: <i>busName</i>_sourceTenant

<i>Required</i>

### 
The name of the tenant to be added to every outgoing message, to identify which tenant sent it.

Default (property): ${<i>systemName</i>.tenant.name}

<i>Required</i>

