# Athena

UNDER DEVELOPMENT!

## Introduction

This is a Service Discovery server made with PHP, using Zend Expressive micro-framework.

It's goal is to provide service discovery via REST API to distributed systems, like in a micro service architeture.

The client library is [Athena-Client](https://github.com/mt-olympus/athena-client) and there will be framework-specific implmentations in the future.

## Workflow Example

* Service A registers itself to the Athena server informing its IP, port, service name (service-test), and some other informations
* At its heartbeat (X seconds since last one), it informs the Athena server that it is still alive
* Service B asks the Athena server to a list of registered services for 'service-a', that answers with information from service A
* Service B connects to service A
* Service C registers itself for the same service as A (service-test)
* When service B asks Athena, it returns both services A AND C
* Service B now can choose between A and C to connect to (Can use [Kharon](https://github.com/mt-olympus/kharon) as load balance)

* Service A and C can unregister itself from Athena server
* Athena server can unregister a service if it stays too long without a heartbeat

 