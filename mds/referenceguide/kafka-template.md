---
id: kafka-template
title: Kafka template
sidebar_label: Kafka template
---

A kafka template wraps a Kafka producer and provides convenience methods to send data to kafka topics.

See documentation for the possible property names and their description.

Required properties: <i>bootstrap.servers</i>, <i>key.serializer</i>, <i>value.serializer</i>

Example values

bootstrap.servers:  <code>localhost:9092</code>
key.serializer:  <code>org.apache.kafka.common.serialization.StringSerializer</code>
value.serializer: <code>org.apache.kafka.common.serialization.StringSerializer</code>

<a href="https://docs.spring.io/spring-kafka/docs/1.3.9.RELEASE/reference/html/_reference.html#_sending_messages" target="_new">Kafka template documentation</a>
<a href="https://kafka.apache.org/documentation/#producerconfigs" target="_new">Producer property documentation</a>
<a href="https://github.com/apache/kafka/tree/0.11.0/clients/src/main/java/org/apache/kafka/common/serialization" target="_new">Serializer class options</a>


