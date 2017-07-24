---
layout: page
title: flink/job
permalink: /job/
---

### How to build `job` project located in my `flink` repo

Clone `flink` repo to your Linux computer with below terminal commands
~~~bash
# Clone
$ git clone https://github.com/bauer/flink.git
~~~

Build `job` with below terminal commands
~~~bash
# Change directory
$ cd flink/job

# Clean project
flink/job$ mvn clean

# Build project
flink/job$ mvn clean install
~~~

The output is located in the `target` folder and is named `job-0.1.jar` or `original-job-0.1.jar` if dependecies are not needed.

---
### Apache Flink WordCount job

The jar file named `job-0.1.jar` from above is required and contains the jobs to execute.

It's assumed Apache Flink version 1.3.1 is available on your computer, if not get it from Apache Flink project on `https://flink.apache.org/`

~~~bash
# Change to installation directory (below is valid for a local 1.3.1 flink build from source code)
$ cd flink/flink-dist/target/flink-1.3.1-bin/flink-1.3.1

# Start Flink on your local computer and get the Flink web at http://localhost:8081
$ bin/start-local.sh

# Execute Flink example job called WordCount
$ bin/flink run -c io.github.bauer.flink.job.WordCount <your-path>/flink/job/target/job-0.1.jar
~~~
---
### Apache Flink Kafka R/W jobs

Note: If you only have default single availble job slot for Flink, then change config to at least 2 available,
by editing the file called flink-conf.yaml, change value for taskmanager.numberOfTaskSlots: from 1 to 2.

Start Flink & Kafka first, then start R/W jobs
~~~bash
# Then execute the Flink job called KafkaWrite to generate some data to Kafka with below
$ bin/flink run -c io.github.bauer.flink.job.KafkaWrite ./../flink/job/target/job-0.1.jar --topic KafkaTest

# and then execute the Flink job called KafkaRead to get some data from Kafka wit below command
$ bin/flink run -c io.github.bauer.flink.job.KafkaRead ./../flink/job/target/job-0.1.jar --topic KafkaTest
~~~

and look for the result
~~~bash
# Apache Flink Dashboard for stdout on the taskmanager should show something simular to below output
Product: "FakeProduct"
Software: "Software-9"
Hardware: "Hardware-0"
Value: 429

Product: "FakeProduct"
Software: "Software-0"
Hardware: "Hardware-1"
Value: 430

Product: "FakeProduct"
Software: "Software-1"
Hardware: "Hardware-2"
Value: 431

Product: "FakeProduct"
Software: "Software-2"
Hardware: "Hardware-0"
Value: 432
~~~
