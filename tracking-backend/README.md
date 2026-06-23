# Smart Campus Tracking System — Backend

This project is a Spring Boot backend (Java 17, Spring Boot 3.x, Maven) implementing REST APIs, MySQL persistence, and a WebSocket (STOMP) live-location feed. It follows the step-by-step guide used for demonstrations.

Quick setup (Windows)

1) Install prerequisites
- Java 17 or later
- Maven (or use the included `mvnw` wrapper)
- MySQL 8.x

2) Create the database and user in MySQL (run in MySQL shell):

```sql
CREATE DATABASE campus_tracking;
CREATE USER 'campus_user'@'localhost' IDENTIFIED BY 'StrongPassword123!';
GRANT ALL PRIVILEGES ON campus_tracking.* TO 'campus_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

If you change the password or username, update `src/main/resources/application.properties` accordingly.

3) Run the application (from project root):

Windows PowerShell:

```powershell
./mvnw spring-boot:run
```

Or with local Maven:

```powershell
mvn spring-boot:run
```

4) Test endpoints (examples):
- Create user: POST http://localhost:8080/api/users
- Post location: POST http://localhost:8080/api/locations
- Mark present: POST http://localhost:8080/api/attendance/present?userId=1&classroomId=A-204

5) Verify WebSocket feed
Open the example `test.html` (create in a browser) and connect to ws://localhost:8080/ws and subscribe to `/topic/locations`.

Notes
- The project uses Lombok — make sure your IDE has Lombok enabled.
- `spring.jpa.hibernate.ddl-auto=update` lets Hibernate create schema automatically for demonstration. Switch to `validate` or use migrations for production.
