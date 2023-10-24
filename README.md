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
![Spring kafka supplier](assets/spring%20kafka%20supplier.gif)

![Kafka Streaming](assets/kafka%20streaming.gif)
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
