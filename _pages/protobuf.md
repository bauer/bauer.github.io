---
layout: page
title: flink/protobuf
permalink: /protobuf/
---

### How to build `protobuf` project located in my `flink` repo

Clone `flink` repo to your Linux computer with below terminal commands
{% highlight bash %}

# Clone
$ git clone https://github.com/bauer/flink.git

{% endhighlight %}

Build `protobuf` with below terminal commands

{% highlight bash %}

# Change directory
$ cd flink/protobuf

# Clean project
flink/protobuf$ mvn clean

# Build project
flink/protobuf$ mvn clean install

{% endhighlight %}

The output is located in the `target` folder and is named `bauer-protobuf-report-1.0-SNAPSHOT.jar`

View generated java code in folder `target/generated-sources/protobuf/java/io/github/bauer`in file named `ProtobufReport.java`
