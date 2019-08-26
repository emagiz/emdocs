---
id: jdbc-channel-message-store
title: JDBC channel message store
sidebar_label: JDBC channel message store
---

# JDBC channel message store
Channel-specific implementation of <code>MessageGroupStore</code> using a relational database via JDBC. This message store shall be used for message channels only.

As such, the JdbcChannelMessageStore uses database specific SQL queries.

Contrary to the JdbcMessageStore, this implementation uses a single database table, optimized to operate like a queue. The SQL scripts for creating the table are packaged under org/springframework/integration/jdbc/schema-*.sql, where * denotes the target database type.



#### Data source
The JDBC DataSource to use when interacting with the database.

#### Query provider
Allows to configure database-specific queries according to the selected database provider.

####  Region
A unique grouping identifier for all messages persisted with this store.

Default value is <code>DEFAULT</code>

#### Table prefix
Public setter for the table prefix property. 

Default value is <code>INT_<code>

#### Using ID cache
Consider using this property when polling the database transactionally using multiple parallel threads, meaning when the configured poller is configured using a task executor.

Default value is <code>false</code>

#### Group capacity
Specifies  the number of messages that the <i>channel message store</i> can persist for a specified channel id. After the capacity limit is reached, the next messages will be discarded.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: jdbc-channel-message-store
title: JDBC channel message store
sidebar_label: JDBC channel message store
---

Channel-specific implementation of <code>MessageGroupStore</code> using a relational database via JDBC. This message store shall be used for message channels only.

As such, the JdbcChannelMessageStore uses database specific SQL queries.

Contrary to the JdbcMessageStore, this implementation uses a single database table, optimized to operate like a queue. The SQL scripts for creating the table are packaged under org/springframework/integration/jdbc/schema-*.sql, where * denotes the target database type.

