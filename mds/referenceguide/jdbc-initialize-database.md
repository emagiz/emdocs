---
id: jdbc-initialize-database
title: JDBC initialize database
sidebar_label: JDBC initialize database
---


# JDBC Initialize database
Use this if you want to initialize a database on startup (or on exit). This can be use for example for table creation and/or population.

The script locations can also be patterns with wildcards in the usual ant style used. (e.g. classpath*:/com/foo/**/sql/*-data.sql). If a pattern is used the scripts are executed in lexical order of their URL or filename.

To use custom SQL scripts, add them to the flow resources and then use the prefix <code>resource/</code> in front of the filename. Uploading the script will change the filename. To find the new filename download the file after uploading it.

eMagiz provides to initialization scripts:

When using a H2 database for a Spring Integration (channel) message store use this location:
<code>classpath:com/emagiz/components/jdbc/int-schema-h2.sql</code>

When using a H2 database for Spring Batch (ETL) use this location:
<code>classpath:com/emagiz/components/jdbc/batch-schema-h2.sql</code>



#### Enabled
If disabled the scripts will not be executed. Defaults to enabled but can be used to switch on and off script execution using deployment properties for example: ${system.database.initialize}. The property should resolve in <code>true</code> or <code>false</code>.

Default is <code>true</code>.

#### Separator
The default statement separator to use. The default is to use <code>;</code> if it is present in the script, or <code>\n</code> (new line) otherwise.

#### Ignore failures
Should failed SQL statements be ignored during execution? The options are:
<ul>
<li><i>None</i>: Do not ignore failures.</li>
<li><i>Drops</i>: Ignore failed DROP statements.</li>
<li><i>All</i>: Ignore all failures.</li>
</ul>

Default is <i>None</i>.

---
id: jdbc-initialize-database
title: JDBC initialize database
sidebar_label: JDBC Initialize database
---

Use this if you want to initialize a database on startup (or on exit). This can be use for example for table creation and/or population.

The script locations can also be patterns with wildcards in the usual ant style used. (e.g. classpath*:/com/foo/**/sql/*-data.sql). If a pattern is used the scripts are executed in lexical order of their URL or filename.

To use custom SQL scripts, add them to the flow resources and then use the prefix <code>resources/</code> in front of the filename. Uploading the script will change the filename. To find the new filename download the file after uploading it.

eMagiz provides to initialization scripts:

When using a H2 database for a Spring Integration (channel) message store use this location:
<code>classpath:com/emagiz/components/jdbc/int-schema-h2.sql</code>

When using a H2 database for Spring Batch (ETL) use this location:
<code>classpath:com/emagiz/components/jdbc/batch-schema-h2.sql</code>



