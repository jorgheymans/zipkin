[![Gitter chat](https://img.shields.io/badge/gitter-join%20chat%20%E2%86%92-brightgreen.svg)](https://gitter.im/openzipkin/zipkin)
[![Build Status](https://travis-ci.org/openzipkin/zipkin.svg?branch=master)](https://travis-ci.org/openzipkin/zipkin) [![Download](https://api.bintray.com/packages/openzipkin/maven/zipkin/images/download.svg) ](https://bintray.com/openzipkin/maven/zipkin/_latestVersion)
[![Maven Central](https://img.shields.io/maven-central/v/io.zipkin/zipkin-server.svg)](https://search.maven.org/search?q=g:io.zipkin%20AND%20a:zipkin-server)

# zipkin
[Zipkin](https://zipkin.io) is a distributed tracing system. It helps gather
timing data needed to troubleshoot latency problems in service architectures.
Features include both the collection and lookup of this data.

If you have a trace ID in a log file, you can jump directly to it. Otherwise,
you can query based on attributes such as service, operation name, tags and
duration. Some interesting data will be summarized for you, such as the
percentage of time spent in a service, and whether or not operations failed.

<img src="https://zipkin.io/public/img/web-screenshot.png" alt="Trace view screenshot" />

The Zipkin UI also presents a Dependency diagram showing how many traced
requests went through each application. This can be helpful for identifying
aggregate behavior including error paths or calls to deprecated services.

<img src="https://zipkin.io/public/img/dependency-graph.png" alt="Dependency graph screenshot" />

Application’s need to be “instrumented” to report trace data to Zipkin. This
usually means configuration of a [tracer or instrumentation library](https://zipkin.io/pages/tracers_instrumentation.html). The most
popular ways to report data to Zipkin are via http or Kafka, though many other
options exist, such as Apache ActiveMQ, gRPC and RabbitMQ. The data served to
the UI is stored in-memory, or persistently with a supported backend such as
Apache Cassandra or Elasticsearch.

## Quick-start
Download the latest release of Zipkin Server using the quickstart script:
```bash
curl -sSL https://zipkin.io/quickstart.sh | bash -s
```
Alternatively use the direct download [link](https://search.maven.org/remote_content?g=io.zipkin&a=zipkin-server&v=LATEST&c=exec).

Now you can start Zipkin Server:
```
java -jar zipkin.jar
```
A Docker image is provided as well:
```bash
docker run -d -p 9411:9411 openzipkin/zipkin
```

Once Zipkin Server is running, you can view traces at `http://your_host:9411/zipkin/` or configure the server endpoint `http://your_host:9411` in your instrumentation library to store traces.

## Next Steps
The [quickstart](#quick-start) section explains how to get Zipkin Server up and running quickly, without any external dependencies. It uses the default in-memory storage component and collects trace data over http. 

Consult the detailed server [documentation](zipkin-server) to learn how to configure your server for realistic workloads, setup persistent storage such as ElasticSearch or Cassandra, add different collector mechanisms (Kafka, RabbitMQ, ...), configure security and much more.

You can now start instrumenting your applications to send trace data to Zipkin Server. Be sure to check out our instrumentation subproject [Brave](https://github.com/openzipkin/brave/), as it provides out of the box instrumentation support for many commonly used components like http, jdbc, jms, kafka, grpc, spring-web and [many more](https://github.com/openzipkin/brave/tree/master/instrumentation). There are also various community supported [tracers] (https://zipkin.io/pages/tracers_instrumentation) available. Or have a look at the various [examples](https://github.com/openzipkin?utf8=%E2%9C%93&q=example) to see in detail how instrumentation is done.

## Maven Artifacts 
Releases are uploaded to [Bintray](https://bintray.com/openzipkin/maven/zipkin) and synchronized to [Maven Central](https://search.maven.org/#search%7Cga%7C1%7Cg%3A%22io.zipkin%22)

Snapshots are uploaded to [JFrog](https://oss.jfrog.org/artifactory/oss-snapshot-local) after commits to master.
## Docker Images
Released versions of zipkin-server are published to Docker Hub as `openzipkin/zipkin`.
See [docker-zipkin](https://github.com/openzipkin/docker-zipkin) for details.
