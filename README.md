# 🍃 Spring Cloud Streams & Kafka 

## Table of Contents
1. [Project Description](#project-description)
2. [Project Structure](#project-structure)
3. [Getting Started](#getting-started)
    - [Downloading Kafka](#downloading-kafka)
    - [Docker Setup](#docker-setup)
4. [Spring Cloud Streams Services](#spring-cloud-streams-services)
    - [Service Producer](#service-producer)
    - [Service Consumer](#service-consumer)
    - [Service Supplier](#service-supplier)
    - [Data Analytics with Kafka Streams](#data-analytics-with-kafka-streams)
5. [Web Application](#web-application)
6. [Project Directory Structure](#project-directory-structure)
7. [Dependencies](#dependencies)
8. [Screenshots](#screenshots)

## Project Description
This project aims to demonstrate real-time data analytics using Kafka and Spring Cloud Streams. It includes the setup of Kafka, a set of Spring Cloud Streams services, and a web application to visualize real-time analytics results.

## Project Structure
The project structure is organized as follows:
```
project-root
├── src
│ ├── main
│ │ ├── java
│ │ │ ├── com.silimanice.springcloudstreamskafka
│ │ │ │ ├── SpringCloudStreamsKafkaApplication.java
│ │ │ │ ├── entities
│ │ │ │ │ ├── PageEvent.java
│ │ │ │ ├── service
│ │ │ │ │ ├── PageEventService.java
│ │ │ │ ├── web
│ │ │ │ │ ├── PageEventRestController.java
│ ├── resources
│ │ ├── application.properties
├── test
│ ├── java
│ │ ├── com.silimanice.springcloudstreamskafka
│ │ ├── SpringCloudStreamsKafkaApplicationTests.java
```

## Getting Started
### Dependencies
List the dependencies used in your project. For example:

- Spring Boot
- Spring Cloud Stream
- Kafka
- Docker
- ...
- 
### Downloading Kafka


To get started, download Kafka and follow these steps:
1. Start Zookeeper:
```
bin\windows\zookeeper-server-start.bat config\zookeeper.properties
```
2. Start Kafka Server:
```
bin\windows\kafka-server-start.bat config\server.properties
```
3. Create a console consumer and supplier for test
```
    start bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic R1
    start bin\windows\kafka-console-producer.bat  --broker-list localhost:9092 --topic R1
```
![Kafka test](assets/kafka%20console%20test.png)
*KAFKA Console Test*

4. Creating a java spring consumer
```java
@Bean
public Consumer<PageEvent> pageEventConsumer() {
  return (input) -> {
      System.out.println("****************************");
      System.out.println(input.toString());
      System.out.println("****************************");
  };
}
```
- Application.properties Configuration
```
spring.cloud.stream.bindings.pageEventConsumer-in-0.destination=R1
spring.cloud.function.definition=pageEventConsumer
```
![Spring Kafka Consumer](assets/kafka%20spring%20consumer.png)
*Spring KAFKA Consumer*

5. Create a java spring supplier
```java
@Bean
public Supplier pageEventSupplier() {
  return () -> new PageEvent(
          Math.random() > 0.5 ? "P1" : "P2",
          Math.random() > 0.5 ? "U1" : "U2",
          new Date(),
          new Random().nextInt(9000));
}
```
- Application.properties configuration
```
spring.cloud.stream.bindings.pageEventSupplier-out-0.destination=R2
spring.cloud.function.definition=pageEventSupplier
spring.integration.poller.fixed-delay=100
```
![Kafka Supplier](assets/spring%20kafka%20supplier.gif)
*Spring KAFKA Supplier*

6. Create a java spring function that can supply and consume at the same time
```java
@Bean
public Function<PageEvent, PageEvent> pageEventFunction() {
  return (input) -> {
      input.setName(input.getName() + " (Modified)");
      input.setUser(input.getUser() + " (Modified)");
      return input;
  };
}
```
- Application.properties
```
spring.cloud.stream.bindings.pageEventFunction-in-0.destination=R1
spring.cloud.stream.bindings.pageEventFunction-out-0.destination=R3
spring.cloud.function.definition=pageEventFunction
```
![Kafka Streaming](assets/kafka%20streaming.gif)
*Spring KAFKA Streaming*

[//]: # (### Docker Setup)

[//]: # (Alternatively, you can use Docker to set up Kafka. Refer to [Confluent's Kafka Docker Quickstart]&#40;https://developer.confluent.io/quickstart/kafka-docker/&#41; or watch [this video]&#40;https://www.youtube.com/watch?v=9O1Kuk2xXO8&#41; for guidance.)

[//]: # ()
[//]: # (## Spring Cloud Streams Services)

[//]: # (### Service Producer)

[//]: # (- Code)

[//]: # (- Screenshots)

[//]: # (### Service Consumer)

[//]: # (- Create a Kafka consumer service.)

[//]: # ()
[//]: # (### Service Supplier)

[//]: # (- Develop a Kafka supplier service.)

[//]: # ()
[//]: # (### Data Analytics with Kafka Streams)

[//]: # (- Build a real-time data analytics service using Kafka Streams.)

[//]: # ()
[//]: # (## Web Application)

[//]: # (- Develop a web application to display real-time analytics results.)

[//]: # ()
[//]: # (## Project Directory Structure)

[//]: # (Explain the project directory structure in detail.)

[//]: # ()
[//]: # ()
[//]: # (## Screenshots)

[//]: # (Include screenshots of the project's user interfaces or relevant components.)
