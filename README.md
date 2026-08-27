# API Gateway

## Overview
The **API Gateway** is a core platform service in the Cloud Trip Gallery microservices architecture. It acts as the single, unified entry point for all external client requests (e.g., the React frontend). It routes incoming traffic to the appropriate backend microservices and handles cross-cutting concerns like CORS and path rewriting.

## Technical Details
* **Technology Stack**: Java 25, Spring Boot, Spring Cloud Gateway
* **Default Port**: `8080`
* **Service Discovery**: Registers with Eureka Server to dynamically resolve backend service instances.
* **Configuration**: Fetches routing configurations centrally from the Config Server.

## Key Responsibilities
* **Routing**: Maps external URLs (e.g., `/trip-service/**`) to internal microservices via `lb://TRIP-SERVICE`.
* **Load Balancing**: Uses Spring Cloud LoadBalancer to distribute requests among multiple instances of a service.
* **CORS Handling**: Manages Cross-Origin Resource Sharing policies to securely allow frontend applications to communicate with the APIs.

## Deployment Context
In the GCP production environment, this service sits behind an External Application Load Balancer and is managed by PM2 within an autoscaling Managed Instance Group (MIG).
