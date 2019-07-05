# SQL Script
SQL script to execute to populate, initialize, or clean up the database.

#### Location
The resource location of an SQL script to execute. Can be a single script location or a pattern (e.g. classpath:/com/foo/sql/*-data.sql

When using a H2 database for a Spring Integration (channel) message store use this location:
<code>classpath:com/emagiz/components/jdbc/int-schema-h2.sql</code>

When using a H2 database for Spring Batch (ETL) use this location:
<code>classpath:com/emagiz/components/jdbc/batch-schema-h2.sql</code>

To use custom SQL scripts, add them to the flow resources and then use the prefix <code>resource/</code> in front of the filename. Uploading the script will change the filename. To find the new filename download the file after uploading it.

#### Encoding
The encoding for SQL scripts, if different from the platform encoding.

#### Separator
The default statement separator to use. The default is to use <code>;</code> if it is present in the script, or <code>\n</code> (new line) otherwise.

#### Execution
Indicate the execution phase of this script. Use <i>Init</i> to execute on startup (as a bean initialization) or <i>Destroy</i> to execute on shutdown (as a bean destruction callback).

Default is <i>Init</i>.

