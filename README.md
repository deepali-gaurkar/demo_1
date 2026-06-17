# Room Web App

A Spring Boot application for managing hotel rooms and employees using Spring Data JPA and an in-memory H2 database.

## Features

* Manage room and employee data
* Spring Data JPA repositories
* H2 in-memory database
* Automatic schema creation and data loading
* H2 web console for querying data
* REST-ready architecture

## Tech Stack

* Java 21
* Spring Boot 3
* Spring Data JPA
* H2 Database
* Maven
* Lombok

## Project Structure

```text
src/main/java
├── controller
├── model
├── repository
└── RoomWebAppApplication.java

src/main/resources
├── application.properties
├── schema.sql
└── data.sql
```

## Getting Started

### Prerequisites

* Java 21
* Maven 3.9+ (optional, Maven Wrapper included)

### Clone the Repository

```bash
git clone <your-repository-url>
cd room-web-app
```

### Run the Application

Using Maven Wrapper:

```bash
./mvnw spring-boot:run
```

The application starts on:

```text
http://localhost:8080
```

## Database Configuration

The application uses an in-memory H2 database.

Configuration:

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

spring.sql.init.mode=always
spring.jpa.hibernate.ddl-auto=none
```

## H2 Console

Open:

```text
http://localhost:8080/h2-console
```

Use the following connection details:

| Property | Value                |
| -------- | -------------------- |
| JDBC URL | `jdbc:h2:mem:testdb` |
| Username | `sa`                 |
| Password | *(leave blank)*      |

## Database Initialization

* `schema.sql` creates the database schema.
* `data.sql` loads sample room and employee data during application startup.

## Sample Queries

```sql
SELECT * FROM ROOMS;

SELECT * FROM EMPLOYEES;

SELECT COUNT(*) FROM ROOMS;

SELECT COUNT(*) FROM EMPLOYEES;
```

## Employee Position Mapping

Employee positions are stored using Java enums and mapped with:

```java
@Enumerated(EnumType.STRING)
private Position position;
```

This stores readable values such as:

* `HOUSEKEEPING`
* `FRONT_DESK`
* `SECURITY`
* `CONCIERGE`

## Build the Project

```bash
./mvnw clean install
```

## Future Enhancements

* Add REST APIs for rooms and employees
* Add service layer
* Add validation and exception handling
* Add integration tests
* Replace H2 with PostgreSQL or MySQL
* Dockerize the application

## License

This project is for learning and demonstration purposes.
