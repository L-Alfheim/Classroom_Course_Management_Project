# Classroom_Course_Management_Project

A Spring Boot demo project for classroom management, providing functionalities such as adding classrooms, querying classroom availability, and adjusting course schedules.

## Features

- Add new classrooms with building number, room number, and capacity level
- Query classroom availability for specific time periods and dates
- Adjust course schedules by updating classroom availability status and associated course information

## Technical Stack

- **Framework**: Spring Boot 3.5.6
- **Database**: MySQL 8.4.0
- **ORM**: Spring Data JPA
- **Build Tool**: Maven
- **Java Version**: 17

## Project Structure

- **Model**: Entity classes representing classroom and availability data (`Classroom`, `ClassroomAvailability`, etc.)
- **DTO**: Data Transfer Objects for request/response handling
- **Repository**: Data access interfaces for database operations
- **Service**: Business logic implementation
- **Controller**: REST API endpoints for handling client requests

## API Endpoints

### Add Classroom
```http
POST /classroom/addclassroom
Content-Type: application/json

{
  "buildingNumber": 45,
  "roomNumber": 107,
  "roomCapacity": "LEVELA"
}
```

### Query Classroom Availability
```http
POST /classroom/query
Content-Type: application/json

{
  "buildingNumber": 45,
  "roomNumber": 107,
  "classPeriod": "Period1",
  "date": "2025-10-24"
}
```

### Adjust Course Schedule
```http
POST /classroom/adjustcourse
Content-Type: application/json

{
  "buildingNumber": 45,
  "roomNumber": 107,
  "classPeriod": "Period1",
  "date": "2025-10-24",
  "isAvailable": false,
  "courseInfo": "05364"
}
```

## Configuration

Database configuration can be modified in `src/main/resources/application.properties`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/twtdemo?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
spring.datasource.username=root
spring.datasource.password=yourPassword
server.port=4165
```

## Getting Started

1. Clone the repository
2. Configure database connection in `application.properties`
3. Build the project using Maven:
   ```bash
   ./mvnw clean package
   ```
4. Run the application:
   ```bash
   java -jar target/twtdemo-1.0.0.jar
   ```
