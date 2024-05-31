# IronHack-Lab9-Microservices-Architecture-

## Tasks:
### Design Exercise:
  * **Application Brief:** Participants are given a description of a monolithic e-commerce application handling user management, product catalog, order processing, and customer support.
  * **Task:** Identify and outline potential microservices based on domain-driven design principles. Participants will determine service boundaries, define how services will communicate, and plan how to handle shared data.

### Monolithic E-Commerce Application Description:
The application is a traditional e-commerce platform that encompasses all functionalities within a single, unified software architecture. The application handles the following key operations:

  * **User Management:** Manages user profiles, authentication, and authorization. It stores personal information, manages login sessions, and handles user preferences.

  * **Product Catalog:** Maintains a comprehensive list of products, including descriptions, pricing, images, and inventory levels. It supports product search and categorization functionalities.

  * **Order Processing:** Manages all aspects of the ordering process, from cart management to order placement, payment processing, and order history tracking.

  * **Customer Support:** Handles customer inquiries, returns, complaints, and feedback through a ticket-based system integrated with the user and order databases.

The application is built on a single relational database that holds all user data, product information, orders, and customer support interactions. It currently operates on a single code base with a web-based frontend that communicates directly with the backend server.

The platform has been experiencing challenges with scaling during high-traffic periods, frequent downtimes during updates, and increasing difficulty in implementing new features without affecting existing functionalities. The goal is to decompose this monolithic architecture into a microservices-based architecture to address these issues and improve overall agility and scalability.

# Implementation Simulation:
  * **Migration Roadmap:** Develop a detailed plan for migrating the identified monolithic components to microservices. This plan should include prioritization of services to be migrated, identification of dependencies, and a strategy for data migration.
  * **Architecture Documentation:** Document the proposed microservices architecture, illustrating the interaction between services and the migration steps. Include a brief narrative explaining the rationale behind key decisions.

# Simulation

  * **Roadmap:**

1. Understanding the problem and planning
    * We need to incrementally refactor the monolithic application. When we incrementally refactor an application, we gradually build a new application that consists of microservices, and run the application along with our monolithic application.

2. Decouple by domain-driven design
    *We can apply the DDD approach retroactively to an existing application as follows:
      * **User Service**
      * **Product Service**
      * **Order Service**
      * **Customer Support Service**
      * **Security**
  
3. Prioritize services for migration:
   * An ideal starting point to decouple services is to identify the loosely coupled modules in our monolithic application. To complete a dependency analysis of each module, we need to look at the following:
   * The type of the dependency: dependencies from data or other modules.
   * The scale of the dependency: how a change in the identified module might impact other modules.

   * The order to procced will be the following:
     3.1 Security
     3.2 Migration of the User Management Service
     3.3 Migration of the Product Service
     3.4 Migration of the Order service
     3.5 Migration of the Customer Support service
   
4. Decomposition:
   * Microservices were defined based on the key functional areas of the monolithic application. This allows clearer management and independent scalability of each component.

5. Asynchronous Communication:
   * Choosing AWS SQS for asynchronous communication allows for greater fault tolerance and decoupling between services. Additionally, it allows us to configure dead letters for order reprocessing.

6.  Data Management:
    * Split the monolithic database based on the service boundaries that we identify.
    * We need to consider other issues, such as data synchronization, transactional integrity, joins, and latency.
     
7.  API Gateway:
     * Set up an API gateway to manage external communication with new microservices.

9.  Deployment:
     * Allows the efficient deployment and management of Docker containers, ensuring scalability and high availability.
     
10.  Monitoring and Observability:
      * Provides comprehensive visibility of the logs and performance of microservices, facilitating the detection and resolution of problems.
    
12. System Integrity:
      * Facilitates user management and improves security by delegating authentication to a specialized service.
   
### Architecture design:

![Architecture_design_ecommerce](https://github.com/LiMonC/IronHack-Lab9-Microservices-Architecture-/assets/6668834/5c0f2327-9472-42fc-b9d2-1d2179080a12)



