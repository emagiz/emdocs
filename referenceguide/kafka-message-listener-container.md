---
id: kafka-message-listener-container
title: Kafka message listener container
sidebar_label: Kafka message listener container
---

A kafka listener container describe the Kafka broker listeners to receive Kafka messages.

See documentation for the possible property names and their description.

Required properties: <i>bootstrap.servers</i>, <i>key.deserializer</i>, <i>value.deserializer</i>, <i>group.id</i>

Example values

bootstrap.servers:  <code>localhost:9092</code>
key.deserializer:  <code>org.apache.kafka.common.serialization.StringDeserializer</code>
value.deserializer: <code>org.apache.kafka.common.serialization.StringDeserializer</code>
group.id: <code>test-consumer-group</code>

<a href="https://docs.spring.io/spring-kafka/docs/1.3.9.RELEASE/reference/html/_reference.html#_receiving_messages" target="_new">Message listener container documentation</a>
<a href="https://kafka.apache.org/documentation/#consumerconfigs" target="_new">Consumer property documentation</a>
<a href="https://github.com/apache/kafka/tree/0.11.0/clients/src/main/java/org/apache/kafka/common/serialization" target="_new">Deserializer class options</a>


---
id: kafka-message-listener-container
title: Kafka message listener container
sidebar_label: Kafka listener container
---

A kafka listener container describes the Kafka broker.

See documentation for the possible property names and their description.

<a href="https://kafka.apache.org/documentation/#consumerconfigs" target="_new">Property documentation</a>

