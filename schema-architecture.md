# Smart Clinic Management System – Architecture Design

## Section 1: Architecture Summary

The Smart Clinic Management System follows a three-tier architecture consisting of Presentation, Application, and Data layers. The system supports both HTML-based dashboards (for Admins and Doctors) and RESTful APIs (for external or dynamic frontend integration). The backend is built using Java with Spring Boot, leveraging MVC architecture for rendering Thymeleaf views and REST controllers for API communication. Data persistence is handled via dual databases: MySQL is used for structured relational data such as doctors, patients, and appointments, while MongoDB is used to store unstructured and flexible data such as medical prescriptions. The system ensures modularity, scalability, and maintainability by separating concerns across layers and using standard Spring technologies and JPA/Mongo integrations.

---

## Section 2: Request-Response Flow (Numbered)

1. **User Request Initiation**  
   A user (Admin/Doctor/Patient) sends a request via a web browser (HTML frontend) or API client (Postman or frontend JS app).

2. **Frontend Routing**  
   - For HTML-based interfaces: Thymeleaf templates are rendered via Spring MVC Controllers.
   - For API-based access: REST Controllers handle incoming JSON requests.

3. **Authentication & Authorization**  
   JWT-based token authentication is verified using Spring Security filters to validate access and determine roles (Admin, Doctor, Patient).

4. **Controller Layer**  
   The request is handled by either:
   - A `@Controller` (MVC) returning a Thymeleaf view, or
   - A `@RestController` returning JSON data.

5. **Service Layer**  
   Controllers delegate logic to services which contain the business logic, validation, and interaction with repositories.

6. **Repository Layer**  
   Services call JPA Repositories (for MySQL) or Mongo Repositories (for MongoDB) to perform CRUD operations.

7. **Data Access Layer**  
   - MySQL handles relational data (e.g., appointments, users, patient details).
   - MongoDB stores dynamic or document-based data like prescriptions.

8. **Database Response**  
   Data is fetched, processed, or updated in the relevant database, and results are returned to the service layer.

9. **Response Construction**  
   The service formats and returns the response:
   - For HTML users: Thymeleaf views with embedded data.
   - For APIs: JSON responses via REST Controller.

10. **Client-Side Rendering**  
   The client (browser or frontend app) receives the response and updates the UI or notifies the user accordingly.






Added architecture design for Smart Clinic app

