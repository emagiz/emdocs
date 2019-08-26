---
id: jdbc-stored-procedure-outbound-gateway
title: JDBC stored procedure outbound gateway
sidebar_label: JDBC stored procedure outbound gateway
---
#### Sends messages to a database and/or receives messages using a stored prodecure.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/jdbc.html#stored-procedure-outbound-gateway" target="_blank">External documentation</a>

Outbound Channel Gateway are used for updating a database using a stored procedure. The response of the stored procedure is used to populate the message on the reply channel.

Results of the gateway can be transformed to xml using the <i>JDBC result transformer</i>.

#### Stored procedure name
Specifies the name of the stored procedure. If the stored procedure is a function, this attribute specifies the function name. 

#### Is a function
If <code>true</code>, a SQL function is called. In that case the <i>stored procedure name</i> attribute defines the name of the called function. 

Defaults to <code>false</code>.

e.g. Functions in PostgreSQL require this attribute to be set to <code>true</code>.

#### SQL data source
Reference to a JDBC data source, usually including some form of connection pooling, used for accessing the database.

<i>Required</i>


Specify the stored procedure or function call input parameters here.

#### Stored procedure name expression
The name of the stored procedure provided as a SpEL expression.

Components that use a message as source of parameters have full access to the message and its headers, in order to derive a stored procedure name.

<i>Optional</i> ; mutually exclusive with <i>stored procedure name</i>.

#### Ignore column meta data
Fully supported databases, can automatically retrieve the parameter definition information for the to be invoked Stored Procedure or Function from the JDBC Meta-data.

However, if the used database does not support meta data lookups or if you like to provide customized parameter definitions, this flag can be set to <code>true</code>. 

It defaults to <code>false</code>.
                            
<b>Fully Supported Databases (Stored Procedures):</b>
 * Apache Derby
 * DB2
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL
 * Sybase

<b>Fully Supported Databases (Functions):</b>
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL

#### Skip undeclared results
If this attribute is set to <code>true</code>, then all results from a stored procedure call that don't have a corresponding <i>SQL parameter definition</i> will be bypassed.

E.g. Stored Procedures may return an update count value, even though your Stored Procedure only declared a single result parameter. The exact behavior depends on the used database.

The value is set on the underlying <code>JdbcTemplate</code>.

Only few developers will probably ever like to process update counts, thus the value defaults to <code>true</code>.

#### Expect single result
This attribute indicates that only one result object shall be returned from the stored procedure/function call. If set to <code>true</code> and the result map from the stored procedure/function call contains only 1 element, then that 1 element is extracted and returned as payload.

If the result map contains more than 1 element and expect single result is <code>true</code>, then a <code>MessagingException</code> is thrown.

Otherwise the complete result map is returned as the payload.

Important Note: Several databases such as H2 are not fully supported for stored procedure and/or function calls.

The H2 database, for example, does not fully support the <code>CallableStatement</code> semantics and when executing function calls against H2, a result list is returned, rather than a single value.

#### Return value required
Indicates the procedure's return value should be included in the results returned.

Default is <code>false</code>.

#### Requires reply
Specify whether this outbound gateway must return a non-<code>null</code> value, i.e. whether every request message must result in a reply message.

If <code>true</code>, a <code>ReplyRequiredException</code> will be thrown when the underlying service returns a <code>null</code> value.

Default is <code>false</code>.

#### JDBC call operations cache size
Defines the maximum number of cached <code>SimpleJdbcCallOperations</code> instances.

Basically, for each stored procedure name a new <code>SimpleJdbcCallOperations</code> instance is created that in return is being cached.

The default cache size is <code>10</code>. A value of <code>0</code> disables caching.

#### Reply timeout
Allows you to specify how long (in milliseconds) this gateway will wait for the reply message to be sent successfully to the reply channel before throwing an exception. This attribute only applies when the channel might block, for example when using a bounded queue channel that is currently full.

Also, keep in mind that when sending to a <i>direct channel</i>, the invocation will occur in the sender's thread. Therefore, the failing of the send operation may be caused by other components further downstream.

If not specified, by default the gateway will wait indefinitely.


SQL parameter definitions define the type and value of each parameter.

If you are using a database that is fully supported, you typically don't have to specify the stored procedure parameter definitions.

Instead, those parameters can be automatically derived from the JDBC meta-data. However, if you are using databases that are not fully supported or if you like to provide customized parameter definitions, you can set those parameters explicitly. See also the <i>ignore column meta-data</i> attribute.

Note that the <i>order</i>, <i>name</i>, <i>type</i>, <i>direction</i> and <i>scale</i> of the SQL parameters should <b>exactly match</b> the settings specified on the database.

#### Request channel
Channel to consume the request messages from.

<i>Required</i>

#### Reply channel
Channel where reply messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the reply messages.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: jdbc-stored-procedure-outbound-gateway
title: JDBC stored procedure outbound gateway
sidebar_label: JDBC stored procedure outbound gateway
---
#### Sends messages to a database and/or receives messages using a stored prodecure.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/jdbc.html#stored-procedure-outbound-gateway" target="_blank">Documentation</a>

Outbound Channel Gateway are used for updating a database using a stored procedure. The response of the stored procedure is used to populate the message on the reply channel.

Results of the gateway can be transformed to xml using the <i>JDBC result transformer</i>.

#### Stored procedure name
Specifies the name of the stored procedure. If the stored procedure is a function, this attribute specifies the function name. 

#### Is a function
If <code>true</code>, a SQL function is called. In that case the <i>stored procedure name</i> attribute defines the name of the called function. 

Defaults to <code>false</code>.

e.g. Functions in PostgreSQL require this attribute to be set to <code>true</code>.

#### SQL data source
Reference to a JDBC data source, usually including some form of connection pooling, used for accessing the database.

<i>Required</i>


Specify the stored procedure or function call input parameters here.

#### Stored procedure name expression
The name of the stored procedure provided as a SpEL expression.

Components that use a message as source of parameters have full access to the message and its headers, in order to derive a stored procedure name.

<i>Optional</i> ; mutually exclusive with <i>stored procedure name</i>.

#### Ignore column meta data
Fully supported databases, can automatically retrieve the parameter definition information for the to be invoked Stored Procedure or Function from the JDBC Meta-data.

However, if the used database does not support meta data lookups or if you like to provide customized parameter definitions, this flag can be set to <code>true</code>. 

It defaults to <code>false</code>.
                            
<b>Fully Supported Databases (Stored Procedures):</b>
 * Apache Derby
 * DB2
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL
 * Sybase

<b>Fully Supported Databases (Functions):</b>
 * MySQL
 * Microsoft SQL Server
 * Oracle
 * PostgreSQL

#### Skip undeclared results
If this attribute is set to <code>true</code>, then all results from a stored procedure call that don't have a corresponding <i>SQL parameter definition</i> will be bypassed.

E.g. Stored Procedures may return an update count value, even though your Stored Procedure only declared a single result parameter. The exact behavior depends on the used database.

The value is set on the underlying <code>JdbcTemplate</code>.

Only few developers will probably ever like to process update counts, thus the value defaults to <code>true</code>.

#### Expect single result
This attribute indicates that only one result object shall be returned from the stored procedure/function call. If set to <code>true</code> and the result map from the stored procedure/function call contains only 1 element, then that 1 element is extracted and returned as payload.

If the result map contains more than 1 element and expect single result is <code>true</code>, then a <code>MessagingException</code> is thrown.

Otherwise the complete result map is returned as the payload.

Important Note: Several databases such as H2 are not fully supported for stored procedure and/or function calls.

The H2 database, for example, does not fully support the <code>CallableStatement</code> semantics and when executing function calls against H2, a result list is returned, rather than a single value.

#### Return value required
Indicates the procedure's return value should be included in the results returned.

Default is <code>false</code>.

#### Requires reply
Specify whether this outbound gateway must return a non-<code>null</code> value, i.e. whether every request message must result in a reply message.

If <code>true</code>, a <code>ReplyRequiredException</code> will be thrown when the underlying service returns a <code>null</code> value.

Default is <code>false</code>.

#### JDBC call operations cache size
Defines the maximum number of cached <code>SimpleJdbcCallOperations</code> instances.

Basically, for each stored procedure name a new <code>SimpleJdbcCallOperations</code> instance is created that in return is being cached.

The default cache size is <code>10</code>. A value of <code>0</code> disables caching.

#### Reply timeout
Allows you to specify how long (in milliseconds) this gateway will wait for the reply message to be sent successfully to the reply channel before throwing an exception. This attribute only applies when the channel might block, for example when using a bounded queue channel that is currently full.

Also, keep in mind that when sending to a <i>direct channel</i>, the invocation will occur in the sender's thread. Therefore, the failing of the send operation may be caused by other components further downstream.

If not specified, by default the gateway will wait indefinitely.


SQL parameter definitions define the type and value of each parameter.

If you are using a database that is fully supported, you typically don't have to specify the stored procedure parameter definitions.

Instead, those parameters can be automatically derived from the JDBC meta-data. However, if you are using databases that are not fully supported or if you like to provide customized parameter definitions, you can set those parameters explicitly. See also the <i>ignore column meta-data</i> attribute.

Note that the <i>order</i>, <i>name</i>, <i>type</i>, <i>direction</i> and <i>scale</i> of the SQL parameters should <b>exactly match</b> the settings specified on the database.

#### Request channel
Channel to consume the request messages from.

<i>Required</i>

#### Reply channel
Channel where reply messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the reply messages.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

