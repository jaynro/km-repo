## Tags- [Apache Kafka with Docker](/apache-spark.md)


# Summary

Apache Kafka is a distributed streaming platform that excels in handling real-time data feeds and building scalable, fault-tolerant data pipelines. Developed by the Apache Software Foundation, Kafka follows a publish-subscribe model, allowing seamless communication between producers and consumers through topics.

In this document we briefly discuss the core concepts of Apache Kafka, however it is enough to give you an overview of how it works.

## Why should we use Apache Kafka? 
There are several compelling reasons to use Apache Kafka, and its popularity has grown significantly due to its unique features and capabilities.

### Key Advantages:

1.	Scalability: Kafka is designed to scale horizontally, accommodating increased data loads by adding more nodes to the cluster. This ensures the system's ability to handle growing demands effortlessly.

2.	Fault tolerance: Kafka ensures data durability by replicating data across multiple nodes. In the event of node failures, data remains accessible, contributing to a robust and reliable streaming infrastructure.

3.	Low latency: The platform offers low-latency processing, making it suitable for applications requiring real-time data streaming. This responsiveness is crucial for various use cases, including financial transactions and monitoring systems.

4.	Versatility: Kafka's flexibility extends to its capability to integrate seamlessly with diverse data sources. It serves as a central hub for streaming data, making it applicable to a wide range of scenarios, from log aggregation to real-time analytics.

5.	Ecosystem and integration: Kafka boasts a rich ecosystem with tools like Kafka Connect for building connectors to external systems and Kafka Streams for developing applications that process and analyze data within the Kafka platform. This extensibility enhances its overall functionality.

6.	Reliable data processing: Organizations benefit from Kafka's reliable data processing capabilities, ensuring that critical information is efficiently managed and delivered in real-time, contributing to improved decision-making processes.

## How Apache Kafka works?
As mentioned above, Apache Kafka works on the principles of a publish-subscribe model and is built to be scalable, fault-tolerant, and highly durable. Here's a high-level overview of how Apache Kafka works:

### Topics and Producers:
Data is organized into topics, which act as channels for communication.
Producers publish records (messages) to specific topics.
Topics can be thought of as feeds to which data is sent.

### Brokers:
Kafka clusters consist of one or more brokers (servers).
Brokers store data and serve client requests.
Each broker is part of the cluster and has its own unique identifier.

### Partitioning:
Each topic is divided into partitions, which allows for parallel processing and scalability.
Partitions are the basic unit of parallelism and data distribution in Kafka.

### Replication:
Each partition has multiple replicas distributed across different brokers.
Replication ensures fault tolerance. If one broker fails, data remains accessible from its replicas.

### Consumers:
Consumers subscribe to topics and process records from partitions.
Consumers can be part of a consumer group, enabling parallel processing and load balancing.

### Zookeeper:
Zookeeper is used for managing and coordinating Kafka brokers.
It maintains metadata, such as topic and partition information, and tracks the health of brokers.

### Publish-Subscribe Model:
Producers publish records to topics without being aware of the consumers.
Consumers subscribe to topics and receive records in real-time.

### Retention and Log Compaction:
Kafka retains records for a configurable period or size.
Log compaction ensures that only the latest record for each key is retained, reducing storage.

### Scalability:
Kafka scales horizontally by adding more brokers to the cluster.
Each broker can handle multiple partitions, and adding more brokers increases the overall capacity.

### Connectors and Streams:
Kafka supports connectors for integrating with external systems, facilitating data import/export.
Kafka Streams allows for building applications that process and analyze data within the Kafka platform.

### Producers and Consumers
In Apache Kafka, producers and consumers play essential roles in the real-time data streaming ecosystem.

Producers are responsible for publishing (or producing) records/messages to Kafka topics, they generate data and send it to Kafka topics, which act as channels or feeds. They are unaware of the number of consumers or who is consuming the data.

Here is a Java example of how Producers work:

```
import org.apache.kafka.clients.producer.*;

// Example 1: Producer sending a message to a Kafka topic
public class KafkaProducerExample {
    public static void main(String[] args) {
        Properties properties = new Properties();
        properties.put("bootstrap.servers", "localhost:9092");
        properties.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
        properties.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");

        Producer<String, String> producer = new KafkaProducer<>(properties);

        ProducerRecord<String, String> record = new ProducerRecord<>("example-topic", "key", "Hello, Kafka!");
        producer.send(record);
        producer.close();
    }
}
```

Consumers by the other hand, subscribe to Kafka topics and process the records/messages published by producers, they retrieve and process data from Kafka topics in real-time.

Here is a Java example of how Consumers work:

```

import org.apache.kafka.clients.consumer.*;
import java.time.Duration;
import java.util.Collections;
import java.util.Properties;

// Example 2: Consumer subscribing to a Kafka topic
public class KafkaConsumerExample {
    public static void main(String[] args) {
        Properties properties = new Properties();
        properties.put("bootstrap.servers", "localhost:9092");
        properties.put("key.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
        properties.put("value.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
        properties.put("group.id", "example-group");

        Consumer<String, String> consumer = new KafkaConsumer<>(properties);
        consumer.subscribe(Collections.singletonList("example-topic"));

        while (true) {
            ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
            records.forEach(record -> {
                System.out.println("Received message: " + record.value());
            });
        }
    }
}
```

### Apache Kafka step by step

If you want to try Apache Kafka by yourself here you have a reference guide step by step about it and some extra example resources.

 * [Apache Kafka with Docker](https://www.baeldung.com/apache-kafka)
 * [Apache Kafka with Springboot](https://github.com/netsurfingzone/Spring-Boot-Kafka-Producer-and-Consumer-Example)
 * [Spring for Apache Kafka](https://spring.io/projects/spring-kafka#overview)
 * [Spring Kafka Samples](https://github.com/spring-projects/spring-kafka/tree/main/samples)

### Related topics
 * [Apache Kafka Streams](https://github.com/hfacundo/km-repo/blob/main/in-progress/apache-kafka-streams.md)
 * [Apache ZooKeeper](https://github.com/hfacundo/km-repo/blob/main/in-progress/apache-zookeeper.md) 
 * [Apache Spark](https://github.com/hfacundo/km-repo/blob/main/in-progress/apache-spark.md)
 * [Apache Hadoop](https://github.com/hfacundo/km-repo/blob/main/in-progress/apache-hadoop.md)
 * Apache Storm
 * Apache Flink
 * [Confluent Cloud](https://github.com/hfacundo/km-repo/blob/main/in-progress/confluent-cloud.md)
 * Spring Kafka
 * Docker
 * Kubernetes
 * [Event Driven architecture](https://github.com/hfacundo/km-repo/blob/main/in-progress/event-driven-architecture.md)
 * Microservices
 * Real-time data processing architecture

