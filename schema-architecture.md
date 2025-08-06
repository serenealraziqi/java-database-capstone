## Section 1: Architecture Summary

This Spring Boot application utilizes a hybrid architecture combining both MVC and REST paradigms. For the administrative and doctor-facing dashboards, the application employs **Thymeleaf templates** that render server-side HTML views, facilitating rich user interfaces for logged-in users like admins and doctors. 

For patient-related modules such as appointment management, patient records, and dashboards, the backend exposes **RESTful APIs**, allowing scalable, stateless client-server interactions supporting mobile apps or other frontend technologies.

The application integrates with two databases to optimize data storage according to data types and access patterns:

- **MySQL**, accessed via Spring Data JPA, stores structured and relational data entities such as patients, doctors, appointments, and admin users. The database schema enforces data integrity with normalized tables.
- **MongoDB**, accessed via Spring Data MongoDB, stores flexible, document-oriented prescription records, accommodating variable data schemas and rapid iteration.

The system is layered as follows: all incoming requests (either Thymeleaf controllers or REST controllers) flow into a shared **service layer** which encapsulates business logic, validation, and orchestration. The service layer accesses repositories corresponding to either MySQL or MongoDB data stores, abstracting data access and persistence. This separation enhances maintainability, scalability, and testability of the application.

## Section 2: Numbered Flow of Data and Control

1. **User Interface Layer**:  
   Users interact through either server-rendered Thymeleaf web dashboards (AdminDashboard and DoctorDashboard) or through REST clients such as mobile apps or modern single-page applications that consume JSON APIs.

2. **Controller Layer**:  
   The application routes incoming HTTP requests based on URL and HTTP method to either Thymeleaf controllers (rendering HTML views) or REST controllers (processing API requests and returning JSON responses).

3. **Service Layer**:  
   Controllers delegate business logic execution and workflow coordination to the service layer. This includes data validation, enforcement of business rules, and transaction management such as verifying doctor availability before booking appointments.

4. **Repository Layer**:  
   The service layer accesses data repositories which abstract database operations. Spring Data JPA repositories interface with MySQL for relational data, while Spring Data MongoDB repositories handle unstructured prescription documents.

5. **Database Access**:  
   Repositories execute queries and commands against their respective databases—MySQL providing structured, relational persistence with ACID compliance, and MongoDB offering flexible document-oriented storage enabling rapid schema changes.

6. **Model Binding**:  
   Data retrieved from the databases is automatically mapped into Java model classes—JPA entities for MySQL tables and document models for MongoDB collections—enabling the application to manipulate data as strongly-typed objects.

7. **Response Generation**:  
   For MVC flows, model data is embedded into Thymeleaf templates and returned as fully rendered HTML pages to users’ browsers. For REST flows, models (or DTOs) are serialized to JSON and delivered to client applications. This completes the end-to-end request and response cycle.
