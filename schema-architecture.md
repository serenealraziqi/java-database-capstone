# Smart Clinic Management System – Architecture Design

## Section 1: Architecture Summary

The Smart Clinic Management System follows a three-tier architecture that separates the system into three core layers: Presentation, Application, and Data. This design improves modularity, maintainability, and scalability. The application is developed using Spring Boot, combining both Spring MVC and REST APIs for handling user interactions.

Thymeleaf is used to serve server-rendered views for Admin and Doctor dashboards, while REST APIs serve dynamic and external client modules such as Patient Dashboards and Appointments. The backend uses a shared Service Layer to apply business logic, regardless of whether the request comes from a controller serving a Thymeleaf view or a REST endpoint.

For persistence, the application integrates two databases:
- **MySQL** is used via Spring Data JPA for structured, relational data such as users, doctors, appointments, and admin records.
- **MongoDB** is accessed via Spring Data MongoDB for storing flexible, document-based data like medical prescriptions.

This tech stack enables the application to support both traditional web and API-based access while maintaining a clean separation of concerns and adhering to Spring Boot best practices. The system is also designed for containerization with Docker and supports CI/CD via GitHub Actions.

---

## Section 2: Numbered Flow – Data and Control Flow

1. **User Access**
   - Users (Admin, Doctor, Patient) access the system via web browsers (Thymeleaf dashboards) or external clients (REST API consumers like mobile apps or JS frontends).

2. **Controller Layer**
   - Requests are routed to either:
     - Spring MVC Controllers for rendering HTML pages via Thymeleaf.
     - REST Controllers for handling JSON-based API calls.

3. **Authentication and Authorization**
   - Incoming requests are validated using JWT tokens via Spring Security.
   - Roles (Admin, Doctor, Patient) are used to enforce access control.

4. **Service Layer**
   - Controllers delegate all core logic to service classes.
   - Business rules are applied here (e.g., checking appointment availability, validating patient IDs).

5. **Repository Layer**
   - The service layer interacts with the appropriate repository:
     - JPA Repositories for MySQL entities like patients, appointments, doctors, and admins.
     - Mongo Repositories for prescriptions stored as documents.

6. **Database Interaction**
   - Repositories query or persist data:
     - MySQL handles normalized relational data with defined schemas and relationships.
     - MongoDB manages flexible and schema-less prescription data.

7. **Response Handling**
   - Retrieved data is returned to the controller.
   - Controllers send the response back to the client:
     - Thymeleaf templates for server-rendered views.
     - JSON objects for REST API consumers.

---


## 📊 Architecture Flow Diagram

```mermaid
graph TD
  A[User (Browser / API Client)] --> B[Controller Layer]
  B --> C[Service Layer]
  C --> D1[JPA Repository (MySQL)]
  C --> D2[Mongo Repository (MongoDB)]
  D1 --> E1[MySQL Database]
  D2 --> E2[MongoDB Database]

  B -.-> F[Thymeleaf Views]
  B -.-> G[REST JSON Response]

  style F fill:#E8F1F8,stroke:#666
  style G fill:#FFF2CC,stroke:#666

5. Scroll down, add a commit message like:






Added architecture design for Smart Clinic app

