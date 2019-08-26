---
id: jdbc-bonecp-data-source
title: JDBC BoneCP data source
sidebar_label: JDBC BoneCP data source
---
#### A data source for SQL databases that connects using JDBC with BoneCP connection pooling.
<a href="http://www.jolbox.com/" target="_blank">External documentation</a>


#### Driver class
The name of the JDBC driver to load. This value is driver specific: for details see the documentation of your JDBC driver.

Some examples of driver names:
- <b>PostgreSQL</b>: <code>org.postgresql.Driver</code>
- <b>MySQL</b>: <code>com.mysql.jdbc.Driver</code>
- <b>SQL Server</b>: <code>com.microsoft.sqlserver.jdbc.SQLServerDriver</code>
- <b>Oracle</b>: <code>oracle.jdbc.OracleDriver</code>
- <b>DB2</b>: <code>com.ibm.db2.jcc.DB2Driver</code>

The JDBC driver must be "installed" before it can be used by eMagiz. While the installation procedure can be different for each driver, usually placing the JDBC <code>.jar</code> library in the eMagiz <code>extensions</code> directory is sufficient.

Note that when running in Mendix, the JDBC drivers that ship with Mendix are always available.

#### JDBC URL
With JDBC, a database is represented by a URL with the following syntax:
<code>jdbc:&lt;subprotocol&gt;:&lt;subname&gt;</code>

The <i>subprotocol</i> is the name of the driver or the name of a database connectivity mechanism. The <i>subname</i> provides a way to identify the data source. The subname can vary, depending on the subprotocol, and it can have any internal syntax the driver writer chooses, including a subsubname. The value for both the <i>subprotocol</i> and the <i>subname</i> are driver specific: for details see the documentation of your JDBC driver.

Some examples of the JDBC URL syntax for different drivers (the <u>underlined</u> words need to be replaced by the correct values):

<b>PostgreSQL</b>
- <code>jdbc:postgresql:<u>database</u></code>
- <code>jdbc:postgresql://<u>host</u>/<u>database</u></code>
- <code>jdbc:postgresql://<u>host</u>:<u>port</u>/<u>database</u></code>

<b>MySQL</b>
- <code>jdbc:mysql:///<u>database</u></code>
- <code>jdbc:mysql://<u>host</u>/<u>database</u></code>
- <code>jdbc:mysql://<u>host</u>:<u>port</u>/<u>database</u></code>

<b>SQL Server</b>
- <code>jdbc:sqlserver://<u>host</u>;databaseName=<u>database</u></code>
- <code>jdbc:sqlserver://<u>host</u>\<u>instance</u>;databaseName=<u>database</u></code>
- <code>jdbc:sqlserver://<u>host</u>\<u>instance</u>:<u>port</u>;databaseName=<u>database</u></code>

<b>Oracle</b>
- <code>jdbc:oracle:thin:@//<u>host</u>/<u>service</u></code>
- <code>jdbc:oracle:thin:@//<u>host</u>:<u>port</u>/<u>service</u></code>

<b>DB2</b>
- <code>jdbc:db2://<u>host</u>/<u>database</u></code>
- <code>jdbc:db2://<u>host</u>:<u>port</u>/<u>database</u></code>

#### Username
Username for connecting to the database.

#### Password
Password for connecting to the database.

#### Partition count
The number of partitions to use.

In order to reduce lock contention and thus improve performance, each incoming connection request picks off a connection from a pool that has thread-affinity, i.e. <code>pool[threadId % partition_count]</code>. The higher this number, the better your performance will be for the case when you have plenty of short-lived threads. Beyond a certain threshold, maintenance of these pools will start to have a negative effect on performance (and only for the case when connections on a partition start running out).

Default is <code>1</code>, minimum is <code>1</code>, recommended is <code>2-4</code> (but very app specific)

#### Max connection per partition
The maximum number of connections that will be contained in every partition.

Setting this to <code>5</code> with 3 partitions means you will have 15 unique connections to the database. Note that the connection pool will not create all these connections in one go but rather start off with <i>min connections per partition</i> and gradually increase connections as required.

Default is <code>20</code>.

#### Min connections per partition
The minimum number of connections that will be contained in every partition.

Default is <code>1</code>.

#### Pool availability threshold
The pool watch thread attempts to maintain a number of connections always available (between <i>min connections</i> and <i>max connections</i>). This value sets the percentage value to maintain. For example, setting it to <code>20</code> means that it tries to keep at least 20% of the pool full of connections.

Setting the value to zero will make the pool create new connections when it needs them but it also means your application may have to wait for new connections to be obtained at times.

Default is <code>20</code> percent.

#### Acquire increment
When the available connections are about to run out, BoneCP will dynamically create new ones in batches. This property controls how many new connections to create in one go (up to a maximum of <i>max connections per partition</i>).

Note: This is a per partition setting.

Default is <code>2</code>.

#### Lazy init
Set to <code>true</code> to force the connection pool to obtain the initial connections lazily.

Default is <code>false</code>.

#### Init SQL
Specifies an initial SQL statement that is run only when a connection is first created.

Has no default value (which disables running an initial SQL statement).

#### Connection timeout
The maximum time (in milliseconds) to wait before a call to <code>getConnection()</code> is timed out. Setting this to zero is similar to setting it to <code>Long.MAX_VALUE</code>.

Default is <code>0</code> (wait forever).

#### Max connection age
Any connections older than this setting will be closed off whether it is idle or not. Connections currently in use will not be affected until they are returned to the pool.

Default is <code>0</code> (no maximum age).

#### Idle connection test period
The time (in seconds) for a connection to remain idle before sending a test query to the DB. This is useful to prevent a DB from timing out connections on its end. Do not use aggressive values here!

Settings this to zero disables sending test queries.

Default is <code>14400</code> (4 hours).

#### Connection test statement
The query to send to the DB to maintain keep-alives and test for dead connections. This is database specific and should be set to a query that consumes the minimal amount of load on the server.

<i>Examples</i>:
MySQL: <code>/* ping *\/ SELECT 1</code>
PostgreSQL: <code>SELECT NOW()</code>

If you do not set this (the default), then BoneCP will issue a metadata request instead that should work on all databases but is probably slower.

Note: in MySQL, prefixing the statement by <code>/* ping *\/</code> makes the driver issue 1 fast packet instead.

Has no default value (metadata request is used instead).

#### Idle max age in seconds
The time (in seconds) for a connection to remain unused before it is closed off. Do not use aggressive values here!

Setting this to zero disables closing unused connections.

Default is <code>3600</code> (1 hour).

#### Release helper threads
The number of helper threads to create that will handle releasing a connection.

When this value is set to zero, the application thread is blocked until the pool is able to perform all the necessary cleanup to recycle the connection and make it available for another thread.

When a non-zero value is set, the pool will create threads that will take care of recycling a connection when it is closed (the application dumps the connection into a temporary queue to be processed asychronously to the application via the release helper threads). Useful when your application is doing lots of work on each connection (i.e. perform an SQL query, do lots of non-DB stuff and perform another query), otherwise will probably slow things down.

Default is <code>3</code>.

#### Disable connection tracking
If set to <code>true</code>, the pool will not monitor connections for proper closure. Enable this option if you only ever obtain your connections via a mechanism that is guaranteed to release the connection back to the pool (e.g. Spring's <code>JdbcTemplate</code>, some kind of transaction manager, etc).

Default is <code>false</code>.

#### Acquire retry attempts
After attempting to acquire a connection and failing, try to connect these many times before giving up.

Default is <code>5</code>.

#### Acquire retry delay
The number of milliseconds to wait before attempting to obtain a connection again after a failure.

Default is <code>7000</code> (seven seconds).

#### Transaction recovery enabled
Set to <code>true</code> to enable recording of all transaction activity and replay the transaction automatically in case of a connection failure.

Default is <code>false</code>.

#### Log statements enabled
If enabled, all SQL statements being executed are logged.

Default is <code>false</code>.

#### Query execute time limit
Queries taking longer than this limit to execute are logged.

Default is <code>0</code> (disables logging).

#### Disable JMX
Set to <code>true</code> to disable JMX.

Default is <code>false</code>.

#### Pool name
The name of the pool for JMX and thread names.

No default value.

#### Statistics enabled
If set to <code>true</code>, keep track of some more statistics for exposure via JMX. Will slow down the pool operation.

Default is <code>false</code>.

#### Default auto-commit
Sets the <i>default auto commit</i> setting for newly created connections.

No default value (driver default is used).

#### Default catalog
Sets the <i>default catalog</i> setting for newly created connections.

No default value (driver default is used).

#### Default read-only
Sets the <i>default read only</i> setting for newly created connections.

No default value (driver default is used).

#### Default transaction isolation
Sets the <i>default transaction isolation</i> setting for newly created connections.

No default value (driver default is used).

#### Statements cache size
The number of statements to cache.

Default is <code>0</code>.

#### Statement release helper threads
The number of statement helper threads to create that will handle releasing a statement.

When this value is set to zero, the application thread is blocked until the pool and JDBC driver are able to close off the statement. When a non-zero value is set, the pool will create threads that will take care of closing off the statement asychronously to the application via the release helper threads). Useful when your application is opening up lots of statements otherwise will probably slow things down.

Default is <code>0</code> (statements are released synchronously).

#### External auth
If set to <code>true</code>, no attempts at passing in a username/password will be attempted when trying to obtain a raw (driver) connection. Useful for cases when you already have another mechanism on authentication e.g. NTLM.

Default is <code>false</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: jdbc-bonecp-data-source
title: JDBC BoneCP data source
sidebar_label: JDBC BoneCP data source
---
#### A data source for SQL databases that connects using JDBC with BoneCP connection pooling.
<a href="http://www.jolbox.com/" target="_blank">Documentation</a>


#### Driver class
The name of the JDBC driver to load. This value is driver specific: for details see the documentation of your JDBC driver.

Some examples of driver names:
- <b>PostgreSQL</b>: <code>org.postgresql.Driver</code>
- <b>MySQL</b>: <code>com.mysql.jdbc.Driver</code>
- <b>SQL Server</b>: <code>com.microsoft.sqlserver.jdbc.SQLServerDriver</code>
- <b>Oracle</b>: <code>oracle.jdbc.OracleDriver</code>
- <b>DB2</b>: <code>com.ibm.db2.jcc.DB2Driver</code>

The JDBC driver must be "installed" before it can be used by eMagiz. While the installation procedure can be different for each driver, usually placing the JDBC <code>.jar</code> library in the eMagiz <code>extensions</code> directory is sufficient.

Note that when running in Mendix, the JDBC drivers that ship with Mendix are always available.

#### JDBC URL
With JDBC, a database is represented by a URL with the following syntax:
<code>jdbc:&lt;subprotocol&gt;:&lt;subname&gt;</code>

The <i>subprotocol</i> is the name of the driver or the name of a database connectivity mechanism. The <i>subname</i> provides a way to identify the data source. The subname can vary, depending on the subprotocol, and it can have any internal syntax the driver writer chooses, including a subsubname. The value for both the <i>subprotocol</i> and the <i>subname</i> are driver specific: for details see the documentation of your JDBC driver.

Some examples of the JDBC URL syntax for different drivers (the <u>underlined</u> words need to be replaced by the correct values):

<b>PostgreSQL</b>
- <code>jdbc:postgresql:<u>database</u></code>
- <code>jdbc:postgresql://<u>host</u>/<u>database</u></code>
- <code>jdbc:postgresql://<u>host</u>:<u>port</u>/<u>database</u></code>

<b>MySQL</b>
- <code>jdbc:mysql:///<u>database</u></code>
- <code>jdbc:mysql://<u>host</u>/<u>database</u></code>
- <code>jdbc:mysql://<u>host</u>:<u>port</u>/<u>database</u></code>

<b>SQL Server</b>
- <code>jdbc:sqlserver://<u>host</u>;databaseName=<u>database</u></code>
- <code>jdbc:sqlserver://<u>host</u>\<u>instance</u>;databaseName=<u>database</u></code>
- <code>jdbc:sqlserver://<u>host</u>\<u>instance</u>:<u>port</u>;databaseName=<u>database</u></code>

<b>Oracle</b>
- <code>jdbc:oracle:thin:@//<u>host</u>/<u>service</u></code>
- <code>jdbc:oracle:thin:@//<u>host</u>:<u>port</u>/<u>service</u></code>

<b>DB2</b>
- <code>jdbc:db2://<u>host</u>/<u>database</u></code>
- <code>jdbc:db2://<u>host</u>:<u>port</u>/<u>database</u></code>

#### Username
Username for connecting to the database.

#### Password
Password for connecting to the database.

#### Partition count
The number of partitions to use.

In order to reduce lock contention and thus improve performance, each incoming connection request picks off a connection from a pool that has thread-affinity, i.e. <code>pool[threadId % partition_count]</code>. The higher this number, the better your performance will be for the case when you have plenty of short-lived threads. Beyond a certain threshold, maintenance of these pools will start to have a negative effect on performance (and only for the case when connections on a partition start running out).

Default is <code>1</code>, minimum is <code>1</code>, recommended is <code>2-4</code> (but very app specific)

#### Max connection per partition
The maximum number of connections that will be contained in every partition.

Setting this to <code>5</code> with 3 partitions means you will have 15 unique connections to the database. Note that the connection pool will not create all these connections in one go but rather start off with <i>min connections per partition</i> and gradually increase connections as required.

Default is <code>20</code>.

#### Min connections per partition
The minimum number of connections that will be contained in every partition.

Default is <code>1</code>.

#### Pool availability threshold
The pool watch thread attempts to maintain a number of connections always available (between <i>min connections</i> and <i>max connections</i>). This value sets the percentage value to maintain. For example, setting it to <code>20</code> means that it tries to keep at least 20% of the pool full of connections.

Setting the value to zero will make the pool create new connections when it needs them but it also means your application may have to wait for new connections to be obtained at times.

Default is <code>20</code> percent.

#### Acquire increment
When the available connections are about to run out, BoneCP will dynamically create new ones in batches. This property controls how many new connections to create in one go (up to a maximum of <i>max connections per partition</i>).

Note: This is a per partition setting.

Default is <code>2</code>.

#### Lazy init
Set to <code>true</code> to force the connection pool to obtain the initial connections lazily.

Default is <code>false</code>.

#### Init SQL
Specifies an initial SQL statement that is run only when a connection is first created.

Has no default value (which disables running an initial SQL statement).

#### Connection timeout
The maximum time (in milliseconds) to wait before a call to <code>getConnection()</code> is timed out. Setting this to zero is similar to setting it to <code>Long.MAX_VALUE</code>.

Default is <code>0</code> (wait forever).

#### Max connection age
Any connections older than this setting will be closed off whether it is idle or not. Connections currently in use will not be affected until they are returned to the pool.

Default is <code>0</code> (no maximum age).

#### Idle connection test period
The time (in seconds) for a connection to remain idle before sending a test query to the DB. This is useful to prevent a DB from timing out connections on its end. Do not use aggressive values here!

Settings this to zero disables sending test queries.

Default is <code>14400</code> (4 hours).

#### Connection test statement
The query to send to the DB to maintain keep-alives and test for dead connections. This is database specific and should be set to a query that consumes the minimal amount of load on the server.

<i>Examples</i>:
MySQL: <code>/* ping *\/ SELECT 1</code>
PostgreSQL: <code>SELECT NOW()</code>

If you do not set this (the default), then BoneCP will issue a metadata request instead that should work on all databases but is probably slower.

Note: in MySQL, prefixing the statement by <code>/* ping *\/</code> makes the driver issue 1 fast packet instead.

Has no default value (metadata request is used instead).

#### Idle max age in seconds
The time (in seconds) for a connection to remain unused before it is closed off. Do not use aggressive values here!

Setting this to zero disables closing unused connections.

Default is <code>3600</code> (1 hour).

#### Release helper threads
The number of helper threads to create that will handle releasing a connection.

When this value is set to zero, the application thread is blocked until the pool is able to perform all the necessary cleanup to recycle the connection and make it available for another thread.

When a non-zero value is set, the pool will create threads that will take care of recycling a connection when it is closed (the application dumps the connection into a temporary queue to be processed asychronously to the application via the release helper threads). Useful when your application is doing lots of work on each connection (i.e. perform an SQL query, do lots of non-DB stuff and perform another query), otherwise will probably slow things down.

Default is <code>3</code>.

#### Disable connection tracking
If set to <code>true</code>, the pool will not monitor connections for proper closure. Enable this option if you only ever obtain your connections via a mechanism that is guaranteed to release the connection back to the pool (e.g. Spring's <code>JdbcTemplate</code>, some kind of transaction manager, etc).

Default is <code>false</code>.

#### Acquire retry attempts
After attempting to acquire a connection and failing, try to connect these many times before giving up.

Default is <code>5</code>.

#### Acquire retry delay
The number of milliseconds to wait before attempting to obtain a connection again after a failure.

Default is <code>7000</code> (seven seconds).

#### Transaction recovery enabled
Set to <code>true</code> to enable recording of all transaction activity and replay the transaction automatically in case of a connection failure.

Default is <code>false</code>.

#### Log statements enabled
If enabled, all SQL statements being executed are logged.

Default is <code>false</code>.

#### Query execute time limit
Queries taking longer than this limit to execute are logged.

Default is <code>0</code> (disables logging).

#### Disable JMX
Set to <code>true</code> to disable JMX.

Default is <code>false</code>.

#### Pool name
The name of the pool for JMX and thread names.

No default value.

#### Statistics enabled
If set to <code>true</code>, keep track of some more statistics for exposure via JMX. Will slow down the pool operation.

Default is <code>false</code>.

#### Default auto-commit
Sets the <i>default auto commit</i> setting for newly created connections.

No default value (driver default is used).

#### Default catalog
Sets the <i>default catalog</i> setting for newly created connections.

No default value (driver default is used).

#### Default read-only
Sets the <i>default read only</i> setting for newly created connections.

No default value (driver default is used).

#### Default transaction isolation
Sets the <i>default transaction isolation</i> setting for newly created connections.

No default value (driver default is used).

#### Statements cache size
The number of statements to cache.

Default is <code>0</code>.

#### Statement release helper threads
The number of statement helper threads to create that will handle releasing a statement.

When this value is set to zero, the application thread is blocked until the pool and JDBC driver are able to close off the statement. When a non-zero value is set, the pool will create threads that will take care of closing off the statement asychronously to the application via the release helper threads). Useful when your application is opening up lots of statements otherwise will probably slow things down.

Default is <code>0</code> (statements are released synchronously).

#### External auth
If set to <code>true</code>, no attempts at passing in a username/password will be attempted when trying to obtain a raw (driver) connection. Useful for cases when you already have another mechanism on authentication e.g. NTLM.

Default is <code>false</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

