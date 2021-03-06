***Batteries included!***

> Using akka-streams, mirror one Kafka topic to another.<br>
Serve as a base building block for any Kafka Stream applications using Scala.<br>
Comes with an SBT config, and a .travis.yml that can publish straight to Docker.

<!-- toc -->

- [Usage](#usage)
  * [`kafka-mirror` on Docker Hub](#kafka-mirror-on-docker-hub)
- [Technical choices & relevant documentation](#technical-choices--relevant-documentation)
- [Other notes](#other-notes)
- [Licence](#licence)

<!-- tocstop -->

# Usage

```
$ sbt new ScalaWilliam/akka-stream-kafka-template.g8
```

And then look at `README.md`.

## `kafka-mirror` on Docker Hub

`kafka-mirror` is automatically built from this template and published to Docker Hub:

* https://hub.docker.com/r/scalawilliam/kafka-mirror/

# Technical choices & relevant documentation

* Configuration options are parsed by [Typesafe Config](https://github.com/typesafehub/config), the defacto configuration library for Scala.
* [akka-stream-kafka Consumer](http://doc.akka.io/docs/akka-stream-kafka/current/consumer.html) wraps the
  [Kafka Consumer](https://www.confluent.io/blog/tutorial-getting-started-with-the-new-apache-kafka-0-9-consumer-client/)
  in a much more usable way.
* The record goes through [akka-streams](http://doc.akka.io/docs/akka/2.4/scala/stream/index.html) with an offset of the input record. Akka streams
provides very powerful streaming abstractions that can be used with [many connectors, including MQTT, AMQP, SQS](http://developer.lightbend.com/docs/alpakka/current/).
* Once the [akka-stream-kafka Producer](http://doc.akka.io/docs/akka-stream-kafka/current/producer.html) pushes the message the consumer offset is committed automatically. This enables resiliency.
* [SBT](http://www.scala-sbt.org/) compiles our source code. Read [Essential SBT](https://www.scalawilliam.com/essential-sbt/) to get more familiar with SBT.
* [sbt-native-packager](http://www.scala-sbt.org/sbt-native-packager/) packages the Scala application into a deployable unit with its dependencies.
* The [sbt-native-packager Docker Plugin](http://www.scala-sbt.org/sbt-native-packager/formats/docker.html) will go the extra mile to build your Docker image and publish it where you ask it to.
* By default Docker ([What is Docker?](https://www.docker.com/what-docker)) will publish to the [Docker Hub](https://docs.docker.com/docker-hub/) which you should sign up to.
* And finally, for logging, we use [logback](https://logback.qos.ch/).


Also, for [`sbt new`](http://www.scala-sbt.org/0.13/docs/sbt-new-and-Templates.html) support:
* Using the [Giter8 templating](http://www.foundweekends.org/giter8/).
* [`sbt new` documentation](http://www.scala-sbt.org/0.13/docs/sbt-new-and-Templates.html).
* One example: https://github.com/typesafehub/stack-examples.g8
* And for reference: https://github.com/lloydmeta/scalameta.g8

# Other notes
To regenerate TOC we use [markdown-toc](https://github.com/jonschlinkert/markdown-toc):

```bash
$ npm install -g markdown-toc
$ markdown-toc -i README.md
```

# Licence
* MIT. Copyright (2016) Apt Elements Ltd. [William Narmontas](https://www.scalawilliam.com/)
