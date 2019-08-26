---
id: jms-queue-configuration
title: JMS queue configuration
sidebar_label: JMS queue configuration
---
#### Specify a JMS queue configuration
<a href="http://docs.jboss.org/hornetq/2.2.14.Final/user-manual/en/html_single/index.html#queue-attributes" target="_blank">External documentation</a>


#### Name
Name of the queue.
By convention, all JMS queues map to core queues where the core queue name has the string jms.queue. prepended to it. E.g. the JMS queue with the name "orders.europe" would map to the core queue with the name "jms.queue.orders.europe".

#### Selector
The selector element defines what JMS message selector the predefined queue will have. Only messages that match the selector will be added to the queue. 
Optional and default is 'null'.

#### Durable
Specifies whether the queue will be persisted. 
Optional and default is true.

