---
id: jdbc-stored-procedure-outbound-channel-adapter
title: JDBC stored procedure outbound channel adapter
sidebar_label: JDBC stored procedure outbound channel adapter
---
#### Sends messages to a database using a stored procedure.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/jdbc.html#stored-procedure-outbound-channel-adapter" target="_blank">External documentation</a>

#### Stored procedure name
Specifies the name of the stored procedure. If the stored procedure is a function, this attribute specifies the function name. 

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

#### JDBC call operations cache size
Defines the maximum number of cached <code>SimpleJdbcCallOperations</code> instances.

Basically, for each stored procedure name a new <code>SimpleJdbcCallOperations</code> instance is created that in return is being cached.

The default cache size is <code>10</code>. A value of <code>0</code> disables caching.


SQL parameter definitions define the type and value of each parameter.

If you are using a database that is fully supported, you typically don't have to specify the stored procedure parameter definitions.

Instead, those parameters can be automatically derived from the JDBC meta-data. However, if you are using databases that are not fully supported or if you like to provide customized parameter definitions, you can set those parameters explicitly. See also the <i>ignore column meta-data</i> attribute.

Note that the <i>order</i>, <i>name</i>, <i>type</i>, <i>direction</i> and <i>scale</i> of the SQL parameters should <b>exactly match</b> the settings specified on the database.

#### Channel
Channel to consume messages from.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

