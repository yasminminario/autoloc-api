# AutoLoc API

Autoloc is a REST API project that demonstrates the implementation of a vehicle rental management system using Spring Boot, JPA, Hibernate, and Spring Security.

## Technologies

- Java 27
- Spring Boot 4
- Maven
- Spring Data JPA & Hibernate
- Microsoft SQL Server
- Spring Security
- Lombok

## Features

- **Vehicle Rental Management:** JPA entities for vehicles, agencies, customers, employees, reservations, contracts, payments, equipment, and maintenance.
- **Database Persistence:** Object-relational mapping with JPA and Hibernate.
- **Entity Relationships:** One-to-One, One-to-Many, Many-to-One, and Many-to-Many associations.
- **Performance Optimization:** LAZY fetching and cascade strategies.
- **Security:** HTTP Basic authentication with role-based authorization (USER and ADMIN).
- **API Testing:** Endpoint validation using Postman.

## Project Structure

- `domain/` — JPA entities and enumerations
- `config/` — Spring Security configuration
- `web/controller/` — REST controllers
- `docs/` — Technical documentation and test evidence

## API Endpoints

| Method | Endpoint | Access |
|---|---|---|
| GET | `/api/public/ping` | Public |
| GET | `/api/hello` | Authenticated |
| GET | `/api/admin/report` | ADMIN only |
