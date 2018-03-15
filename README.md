# sbgracefulsd
Graceful shutdown test for a Spring Boot application running on ECS.

## Intent
Create a Spring Boot application running on ECS, so that when the services are 
drained, the application will process on in flight transactions before shutting down
the SpringBoot application and then terminate the service.

###Spring Boot Application
1.  Supports /helloworld http end point that will respond after 500ms delay
and respond back a random number.
1.  Containerize this application and deploy this on an ECS, behind and ELB.
1.  Run a 10TPS, 100TPS and 1000TPS load against the ELB/Route53.
1.  While the test is running, shutdown one or more services and there should 
be NO errors on jMeter.
