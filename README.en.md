# Service Discovery

![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.4-6DB33F?logo=springboot&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-2025.0.0-6DB33F?logo=spring&logoColor=white)
![Eureka Server](https://img.shields.io/badge/Eureka-Server-E50914?logo=netflix&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.9%2B-C71A36?logo=apachemaven&logoColor=white)
![JaCoCo](https://img.shields.io/badge/JaCoCo-Coverage-success)
![Codecov](https://img.shields.io/badge/Codecov-enabled-F01F7A?logo=codecov&logoColor=white)

[PT-BR](README.md) | [EN](README.en.md)

Service discovery server based on Eureka for the voting microservices ecosystem.

## Overview

- Project: `discovery`
- Default port: `8761`
- Java: `17`
- Spring Boot: `3.5.4`
- Spring Cloud: `2025.0.0`

## Tech Stack

- Spring Boot
- Eureka Server (Netflix)
- Maven
- JaCoCo
- Checkstyle
- PMD
- SpotBugs

## Requirements

- JDK 17
- Maven 3.9+ (or use wrapper `mvnw`)

## Configuration

Main config file: `src/main/resources/application.properties`

```properties
server.port=8761
spring.application.name=discovery
eureka.client.registerWithEureka=false
eureka.client.fetchRegistry=false
eureka.instance.hostname=localhost
```

## Run Locally

### Windows (PowerShell)

```powershell
.\mvnw spring-boot:run
```

### Linux/macOS

```bash
./mvnw spring-boot:run
```

## Build and Tests

```bash
./mvnw clean package
```

## Code Quality

```bash
./mvnw checkstyle:check
./mvnw pmd:check
./mvnw spotbugs:check
```

Note: in the current CI workflow, `spotless:check` is commented out for this module.

## Test Coverage

```bash
./mvnw jacoco:report
```

Report location:

- `target/site/jacoco/index.html`

## CI Pipeline

Main workflow:

- `.github/workflows/workflow-backend-discovery.yml`

Main stages:

- Lint/quality: Checkstyle, PMD, SpotBugs
- Tests + JaCoCo
- Codecov upload
- Artifact build (`target/*.jar`)

## Eureka Dashboard

- URL: `http://localhost:8761/`

With discovery running, other services can register and be dynamically resolved by the gateway.

## License

Internal usage for study/challenge purposes.
