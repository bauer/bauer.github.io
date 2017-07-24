---
layout: page
title: kafka
permalink: /kafka/
---

### How to start Kafka stream platform

~~~bash
# Download binary of Kafka distrubution and extract content and enter that folder
https://kafka.apache.org/downloads

# Use Quickstart guide to get it running if needed
https://kafka.apache.org/quickstart

# In short, start services
$ ./bin/zookeeper-server-start.sh config/zookeeper.properties &
$ ./bin/kafka-server-start.sh config/server.properties &
~~~

Test
~~~bash
# Start Example Producer (in a new terminal for test only)
$ ./bin/kafka-console-producer.sh --topic test --broker-list localhost:9092

# Start Example Consumer (in a new terminal for test only)
$ ./bin/kafka-console-consumer.sh --topic test  --zookeeper localhost:2181

~~~
