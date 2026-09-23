# Hello World API

A simple Spring Boot REST API application that provides a "Hello World" endpoint.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- **Java Development Kit (JDK) 17** or higher
  - Download from [Oracle](https://www.oracle.com/java/technologies/downloads/) or [OpenJDK](https://adoptium.net/)
  - Verify installation: `java -version`
- **Gradle** (optional - the project includes Gradle Wrapper)
  - If not using wrapper, download from [Gradle](https://gradle.org/install/)

## Project Structure

```
helloworld-api/
├── src/
│   ├── main/
│   │   ├── java/com/ibm/helloworld/
│   │   │   ├── HelloWorldApplication.java
│   │   │   └── controller/
│   │   │       └── HelloWorldController.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/com/ibm/helloworld/
├── build.gradle
├── settings.gradle
└── gradlew.bat
```

## Setup Instructions

### 1. Clone or Download the Repository

If you haven't already, navigate to the project directory:

```bash
cd ibm-repos/helloworld-api
```

### 2. Verify Java Installation

Ensure Java 17 or higher is installed:

```bash
java -version
```

Expected output should show version 17 or higher.

## Running the Application

### Option 1: Using Gradle Wrapper (Recommended for Windows)

The project includes a Gradle Wrapper, so you don't need to install Gradle separately.

```bash
# Build the project
gradlew.bat build

# Run the application
gradlew.bat bootRun
```

### Option 2: Using Gradle (if installed)

```bash
# Build the project
gradle build

# Run the application
gradle bootRun
```

### Option 3: Running the JAR file

```bash
# Build the JAR
gradlew.bat build

# Run the JAR
java -jar build/libs/helloworld-api-1.0.0.jar
```

## Verifying the Application

Once the application starts successfully, you should see output similar to:

```
Started HelloWorldApplication in X.XXX seconds
```

The application runs on **port 8080** by default.

### Test the Endpoints

Open your browser or use curl/Postman to test:

1. **Hello World Endpoint**
   ```bash
   curl http://localhost:8080/v1/hello
   ```
   Expected response: `Hello, World!`

2. **Health Check Endpoint**
   ```bash
   curl http://localhost:8080/actuator/health
   ```
   Expected response: JSON with health status

## Running Tests

Execute the test suite:

```bash
# Using Gradle Wrapper
gradlew.bat test

# Using Gradle
gradle test
```

## Configuration

The application configuration is located in `src/main/resources/application.properties`:

- **Server Port**: 8080 (default)
- **Application Name**: helloworld-api
- **Actuator Endpoints**: Health endpoint enabled

To change the port, modify `application.properties`:

```properties
server.port=9090
```

## Stopping the Application

Press `Ctrl + C` in the terminal where the application is running.

## Troubleshooting

### Port Already in Use

If port 8080 is already in use, you'll see an error. Solutions:

1. Change the port in `application.properties`
2. Stop the application using port 8080
3. Use a different port: `gradlew.bat bootRun --args='--server.port=9090'`

### Java Version Issues

Ensure you're using Java 17 or higher:

```bash
java -version
```

If using an older version, update your JDK.

### Build Failures

Clean and rebuild:

```bash
gradlew.bat clean build
```

## Technology Stack

- **Java**: 17
- **Spring Boot**: 3.1.5
- **Spring Web**: REST API support
- **Spring Boot Actuator**: Health monitoring
- **JUnit Jupiter**: Testing framework
- **Gradle**: Build tool

## API Documentation

### Endpoints

| Method | Endpoint | Description | Response |
|--------|----------|-------------|----------|
| GET | `/v1/hello` | Returns a greeting message | `Hello, World!` |
| GET | `/actuator/health` | Health check endpoint | JSON health status |

## Development

### Building for Production

```bash
gradlew.bat build -x test
```

This creates an executable JAR in `build/libs/`.

### IDE Setup

Import the project as a Gradle project in your IDE:

- **IntelliJ IDEA**: File → Open → Select `build.gradle`
- **Eclipse**: File → Import → Gradle → Existing Gradle Project
- **VS Code**: Open folder and install Java Extension Pack

## License

Internal IBM project.

---

**Made with Bob**