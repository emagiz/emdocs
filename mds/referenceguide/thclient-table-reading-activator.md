---
id: thclient-table-reading-activator
title: ThClient table reading activator
sidebar_label: ThClient table reading activator
---
#### Reads records from a single 'ThClient' database table based on header values on the input message.
Reads records from the specified database table using the given <i>offset</i> and <i>limit</i>. This method reads records starting from the beginning of the table (as determined by <code>GetFirst</code>) in database order (as determined by <code>GetNext</code>).

Only the columns specified in the configuration of the <i>ThClient connector</i> are returned in the result set.

The input message must contain the following message headers:
- <b>emagiz_thclient_database</b>: the database to connect with; can be a <code>String</code> containing the database name defined in the configuration, a <code>Number</code> containing the database code defined in the configuration or an actual <code>DatabaseDefinition</code> instance
- <b>emagiz_thclient_table</b>: the table to read records from; can be a <code>String</code> containing the table name defined in the configuration, a <code>Number</code> containing the table code defined in the configuration or an actual <code>TableDefinition</code> instance
- <b>emagiz_thclient_offset</b> (int): offset (in number of records) from the beginning of the table where to start reading; negative values are treated as being zero (no offset)
- <b>emagiz_thclient_limit</b> (int): the maximum number of records to read; use <code>-1</code> for "unlimited", other negative values are treated as being zero

The output message is a <code>Map</code> containing the following key/value pairs:
- <b>&lt;table name&gt;</b> (exactly one): the records that were read from the table as a <code>List</code> containing the records, with each record being a <code>Map</code> of column names / field value pairs
- <b>_hasMore</b>: a boolean indicating whether there were any more records in the table that weren't read after reaching the specified limit (not including records skipped because of the specified offset)
- <b>_nextOffset</b> (optional): an integer indicating the value for the offset that should be used in a subsequent call to retrieve the next set of records; only available when <code>_hasMore</code> is <code>true</code>

The above output format is compatible with the input format of the <i>JDBC result set to XML transformer</i>.

#### ThClient connector
A fully configurated <code>ThClientConnector</code> that this service activator will use to establish database connections.

<i>Required</i>

#### Method
Name of the Java method that will be called when a message is received.

The payload of the message will be passed to this method as a parameter. If the method has a return value, this will be used as the payload for the response message.

#### Requires reply
Specify whether the service method must return a non-null value. This value will be <code>false</code> by default, but if set to <code>true</code>, a <code>ReplyRequiredException</code> will be thrown when the underlying service method returns a <code>null</code> value.

#### Send timeout
Specify the maximum amount of time in milliseconds to wait when sending a reply message to the output channel.

By default the send will block for one second.


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: thclient-table-reading-activator
title: ThClient table reading activator
sidebar_label: ThClient table reading activator
---
#### Reads records from a single 'ThClient' database table based on header values on the input message.
Reads records from the specified database table using the given <i>offset</i> and <i>limit</i>. This method reads records starting from the beginning of the table (as determined by <code>GetFirst</code>) in database order (as determined by <code>GetNext</code>).

Only the columns specified in the configuration of the <i>ThClient connector</i> are returned in the result set.

The input message must contain the following message headers:
- <b>emagiz_thclient_database</b>: the database to connect with; can be a <code>String</code> containing the database name defined in the configuration, a <code>Number</code> containing the database code defined in the configuration or an actual <code>DatabaseDefinition</code> instance
- <b>emagiz_thclient_table</b>: the table to read records from; can be a <code>String</code> containing the table name defined in the configuration, a <code>Number</code> containing the table code defined in the configuration or an actual <code>TableDefinition</code> instance
- <b>emagiz_thclient_offset</b> (int): offset (in number of records) from the beginning of the table where to start reading; negative values are treated as being zero (no offset)
- <b>emagiz_thclient_limit</b> (int): the maximum number of records to read; use <code>-1</code> for "unlimited", other negative values are treated as being zero

The output message is a <code>Map</code> containing the following key/value pairs:
- <b>&lt;table name&gt;</b> (exactly one): the records that were read from the table as a <code>List</code> containing the records, with each record being a <code>Map</code> of column names / field value pairs
- <b>_hasMore</b>: a boolean indicating whether there were any more records in the table that weren't read after reaching the specified limit (not including records skipped because of the specified offset)
- <b>_nextOffset</b> (optional): an integer indicating the value for the offset that should be used in a subsequent call to retrieve the next set of records; only available when <code>_hasMore</code> is <code>true</code>

The above output format is compatible with the input format of the <i>JDBC result set to XML transformer</i>.

#### ThClient connector
A fully configurated <code>ThClientConnector</code> that this service activator will use to establish database connections.

<i>Required</i>

#### Method
Name of the Java method that will be called when a message is received.

The payload of the message will be passed to this method as a parameter. If the method has a return value, this will be used as the payload for the response message.

#### Requires reply
Specify whether the service method must return a non-null value. This value will be <code>false</code> by default, but if set to <code>true</code>, a <code>ReplyRequiredException</code> will be thrown when the underlying service method returns a <code>null</code> value.

#### Send timeout
Specify the maximum amount of time in milliseconds to wait when sending a reply message to the output channel.

By default the send will block for one second.


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

