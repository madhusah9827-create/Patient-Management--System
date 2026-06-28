# Patient Management System

A RESTful web application developed using Spring Boot and MongoDB to manage patient information. The system supports complete CRUD (Create, Read, Update, Delete) operations through REST APIs. This project is designed as a learning project to demonstrate Spring Boot development with a layered architecture project reference.

## Developed by
Madhu Sah 

## Project Architecture

```
src/main/java/com/patientmgmt
├── controller   ← REST endpoints (@RestController)
├── service      ← Business logic (@Component)
├── repository   ← MongoDB data access (MongoRepository)
└── entity       ← Patient model (@Id)
```

## Prerequisites

1. JDK 17 or higher (tested with JDK 25)
2. MongoDB running locally on port 27017, or a MongoDB Atlas connection string
3. Git
4. Postman, Insomnia, or cURL for API testing

## Setup

### 1. Configure MongoDB

Edit `src/main/resources/application.properties`:

```properties
# Local MongoDB (default)
spring.mongodb.uri=mongodb://localhost:27017/patientdb

# MongoDB Atlas (optional)
# spring.data.mongodb.uri=mongodb+srv://<username>:<password>@cluster0.xxxxxx.mongodb.net/patientdb?retryWrites=true&w=majority
```

### 2. Build

```bash
./mvnw clean install
```

### 3. Run

```bash
./mvnw spring-boot:run
```

The API runs at `http://localhost:8080`.

## API Endpoints

| Method | URL | Description |
|--------|-----|-------------|
| GET | `/hello` | Health check |
| GET | `/patient` | Get all patients |
| GET | `/patient/id/{id}` | Get patient by ID |
| POST | `/patient` | Create a patient |
| PUT | `/patient/id/{id}` | Update a patient |
| DELETE | `/patient/id/{id}` | Delete a patient |

### Create Patient (POST)

**URL:** `http://localhost:8080/patient`

```json
{
  "name": "John Doe",
  "age": 35,
  "gender": "Male",
  "phone": "9801234567",
  "diagnosis": "Hypertension"
}
```

### Update Patient (PUT)

**URL:** `http://localhost:8080/patient/id/{id}`

```json
{
  "name": "John Doe",
  "age": 36,
  "gender": "Male",
  "phone": "9801234567",
  "diagnosis": "Controlled Hypertension"
}
```
### Get All Patients (GET)

**URL:** `http://localhost:8080/patient`

**Example Response:**

```json
[
  {
    "id": "6850ab12c1234567890abcd",
    "name": "John Doe",
    "age": 35,
    "gender": "Male",
    "phone": "9801234567",
    "diagnosis": "Hypertension"
  }
]
```
### Get Patient by ID (GET)

**URL:** `http://localhost:8080/patient/id/{id}`

**Example:**
`http://localhost:8080/patient/id/6850ab12c1234567890abcd`

**Example Response:**

```json
{
  "id": "6850ab12c1234567890abcd",
  "name": "John Doe",
  "age": 35,
  "gender": "Male",
  "phone": "9801234567",
  "diagnosis": "Hypertension"
}
```
### Delete Patient (DELETE)

**URL:** `http://localhost:8080/patient/id/{id}`

**Example:**
`http://localhost:8080/patient/id/6850ab12c1234567890abcd`

**Example Response:**

```text
Patient deleted successfully.
```

## Troubleshooting
MongoDB connection refused: Start MongoDB locally (brew services start mongodb-community) 
or update the URI for Atlas.
Port 8080 in use: Add server.port=8081 to application.properties.
