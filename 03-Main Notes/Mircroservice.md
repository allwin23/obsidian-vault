[Course Introduction](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/b6hg7/course-introduction?trk_ref=coach_copy)  Mar 19, 2026

This course focuses on the essential technologies of microservices and serverless computing for cloud-native application development.

**Microservices Architecture**

- Microservices break down large applications (monoliths) into smaller, independently maintainable components.
- This architecture enhances scalability, simplifies maintenance, and offers cost benefits, making it popular among large software organizations.

**Serverless Computing**

- Serverless allows developers to run applications without managing the underlying infrastructure, enabling quick deployment and resource efficiency.
- Applications can automatically free up resources when not in use, streamlining operations.

**Course Structure**

- Module 1: Overview of Microservices and their benefits.
- Module 2: Creation of RESTful APIs, essential for microservices.
- Module 3: Introduction to the Serverless framework and various platforms.
- Module 4: Hands-on experience with IBM Cloud's Code Engine for deploying microservices.
- Module 5: Final project to create and deploy a microservices-based application using serverless technologies.
  
  [Twelve-Factor App Methodology](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/plf5j/twelve-factor-app-methodology?trk_ref=coach_copy)  Mar 19, 2026

The course content focuses on the Twelve-Factor App Methodology, which is essential for modern software development, particularly for web applications delivered as a service.

Code Phase Factors

- **Factor 1: Codebase** - Each application should have a single codebase tracked in a version control system, with multiple deploys possible.
- **Factor 2: Dependencies** - All dependencies must be explicitly declared to ensure reliability and ease of setup for new developers.

Deploy Phase Factors

- **Factor 3: Config** - Configuration should be stored in environment variables to accommodate different deployment environments.
- **Factor 4: Backend Services** - Both local and third-party services should be treated equally, allowing easy swapping without code changes.

Operate Phase Factors

- **Factor 8: Concurrency** - Applications should run concurrent processes to handle increased load without interdependencies.
- **Factor 12: Admin Processes** - Admin tasks should run against the same codebase and configuration to maintain synchronization with the application.

This methodology helps create efficient, scalable, and maintainable software applications.
[What are Microservices?](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/UcN2s/what-are-microservices?trk_ref=coach_copy)  Mar 19, 2026

The content focuses on understanding microservices architecture and its benefits.

Microservices Overview

- Microservices architecture involves breaking down a single application into many smaller, independently deployable services.
- Each service can have its own technology stack, allowing teams to use different programming languages and databases.

Benefits of Microservices

- Microservices enable easier updates and feature additions without affecting the entire application due to their loose coupling.
- They allow for independent scaling of components, reducing infrastructure costs and improving efficiency.

Communication and Scaling

- Services communicate through APIs, event streaming, and message brokers, organized by business functionality.
- Horizontal scaling is emphasized, where individual services can be scaled by adding more instances, enhancing performance without scaling the entire application.
- 
  
  
  [Comparison of Monolith vs. SOA vs. Microservices](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/DrpUR/comparison-of-monolith-vs-soa-vs-microservices?trk_ref=coach_copy)  Mar 19, 2026

The content focuses on comparing three architectural styles: Monolith, Service Oriented Architecture (SOA), and Microservices.

Monolithic Architecture

- A monolithic application contains all functionalities within a single process, making it simpler to manage but harder to modify as it grows.
- An example is a Windows Forms Application, where the user interface, business logic, and data access are all in one codebase.

Service Oriented Architecture (SOA)

- SOA is built on a service provider and consumer model, allowing for discrete units of functionality that can be reused.
- It consists of three components: interface, contract, and implementation, which enhance reliability but can complicate rapid development.

Microservices Architecture

- Microservices are loosely coupled, independent components that allow for targeted scalability and flexibility.
- Each microservice can have its own security and technology stack, but this independence can complicate debugging and security management.

Overall, the video highlights the interconnectedness of monolithic design, the integration capabilities of SOA, and the scalability of microservices. 

[Microservices Patterns](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/hrqIe/microservices-patterns?trk_ref=coach_copy)  Mar 19, 2026

The course content focuses on various patterns used in microservices architecture, highlighting their applications and benefits.

Microservices Patterns

- **Single-Page Application (SPA) Pattern**: This pattern allows users to interact with a web application without reloading the page, enhancing user experience through dynamic service calls to backend services.
- **Backend for Frontend (BFF) Pattern**: This pattern creates a tailored backend for different user interfaces, optimizing performance and user experience across various devices, such as mobile and desktop.

Refactoring and Service Discovery

- **Strangler Pattern**: This approach facilitates the gradual refactoring of monolithic applications into microservices by replacing parts of the application one domain at a time while keeping the original application functional.
- **Service Discovery Pattern**: This pattern enables microservices to locate and communicate with each other dynamically, essential for maintaining service availability and load balancing.

Additional Patterns

- **Entity and Aggregate Pattern**: Useful in scenarios like e-commerce, where an order can be seen as an aggregate of products.
- **Adapter Pattern**: This pattern helps integrate incompatible systems, similar to how plug adapters work for different electrical outlets.

Overall, the lecture emphasizes the importance of these patterns in 
[What is REST?](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/DyPop/what-is-rest?trk_ref=coach_copy)  Mar 19, 2026

The content focuses on understanding RESTful APIs and their significance in application development.

Characteristics of RESTful APIs

- REST stands for Representational State Transfer and is an architectural style for application communication.
- Key characteristics include managing requests through HTTP, providing stateless client-server communication, and having a uniform interface.

Functionality of REST APIs

- REST APIs perform standard functions like creating, reading, updating, and deleting records (CRUD) using HTTP methods: POST, GET, PUT, and DELETE.
- Each request is stateless, meaning it contains all necessary information for processing without relying on stored server context.

Benefits of REST APIs

- The uniform interface ensures consistent data representation across different requests.
- REST APIs are scalable due to their stateless nature, allowing for efficient handling of requests and resources.

[Introduction to API Gateway](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/vJCLd/introduction-to-api-gateway?trk_ref=coach_copy)  Mar 19, 2026

The content focuses on the concept and functionality of an API Gateway in application development.

API Gateway Overview

- An API Gateway is a management tool that acts as an intermediary between clients and backend services, simplifying access to multiple microservices.
- It provides a single point of contact for clients, allowing seamless addition or removal of APIs without client awareness.

Benefits of Using an API Gateway

- It insulates clients from the complexity of microservices architecture, reducing the number of requests needed to retrieve data.
- The gateway enhances security, offers analytics, and allows for monetization of APIs through billing systems.

Drawbacks of Using an API Gateway

- It introduces an additional component that requires maintenance and can become a single point of failure if not designed properly.
- The added network step may increase response times for client requests.

Available API Gateway Products

- Various managed and open-source API Gateway products are available, including IBM DataPower Gateway, Google Apigee, Microsoft Azure, and popular open-source options like Kong and Apache APISIX.
  
  
  [[Graphsql]]
- 
  
  [Introduction to Serverless Computing](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/Hvcf7/introduction-to-serverless-computing?trk_ref=coach_copy)  Mar 19, 2026

**Serverless computing** is defined as the concept of building and running applications that do not require server management. In this model, the responsibility for infrastructure management is offloaded to cloud providers, allowing developers to focus on writing application code.

Key points include:

- Applications are deployed as functions that are executed, scaled, and billed based on demand.
- It combines **Function-as-a-Service (FaaS)** platforms and **Backend-as-a-Service (BaaS)** services.
- Users are billed only for the actual usage, not for idle server time.

This approach leads to faster deployments and increased productivity for developers.

[The Serverless Framework](https://www.coursera.org/learn/applications-development-microservices-serverless-openshift/lecture/HhcEI/the-serverless-framework?trk_ref=coach_copy)  Mar 19, 2026

The **Serverless Framework** is a free and open-source web framework designed to simplify the development and deployment of serverless applications. Here are some key points about it:

- **Purpose**: It allows developers to build and manage serverless applications without worrying about the underlying infrastructure.
- **Supported Providers**: While it was initially designed for AWS Lambda, it also supports other cloud providers like Microsoft Azure, Google Cloud Platform, and Apache OpenWhisk.
- **Command Line Interface (CLI)**: The framework provides a CLI that helps automate tasks, structure projects, and implement best practices.
- **Functionality**: Developers can create functions (small units of code) that are triggered by events, such as HTTP requests or file uploads, and manage resources needed for these functions.
- **Configuration**: Applications are organized through a configuration file (serverless.yml), where developers define functions, events, and resources for deployment.

This framework is particularly useful for building event-driven architectures and microservices.