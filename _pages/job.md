---
layout: page
title: flink/job
permalink: /job/
---

### How to build `job` project located in my `flink` repo

Clone `flink` repo to your Linux computer with below terminal commands
{% highlight bash %}

# Clone
$ git clone https://github.com/bauer/flink.git

{% endhighlight %}

Build `job` with below terminal commands

{% highlight bash %}

# Change directory
$ cd flink/job

# Clean project
flink/job$ mvn clean

# Build project
flink/job$ mvn clean install

{% endhighlight %}

The output is located in the `target` folder and is named `job-0.1.jar` or `original-job-0.1.jar` if dependecies are not needed.


### How to run `job` project with Apache Flink

The jar file named `job-0.1.jar` from above is required and contains the jobs to execute.

It's assumed Apache Flink version 1.3.1 is available on your computer, if not get it from Apache Flink project on `https://flink.apache.org/`

{% highlight bash %}

# Change to installation directory (below is valid for a local 1.3.1 flink build from source code)
$ cd flink/flink-dist/target/flink-1.3.1-bin/flink-1.3.1

# Start Flink on your local computer and get the Flink web at http://localhost:8081
$ bin/start-local.sh

# Execute Flink example job called WordCount
$ bin/flink run -c io.github.bauer.flink.job.WordCount <your-path>/flink/job/target/job-0.1.jar

{% endhighlight %}
