# Service Discovery

![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.4-6DB33F?logo=springboot&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-2025.0.0-6DB33F?logo=spring&logoColor=white)
![Eureka Server](https://img.shields.io/badge/Eureka-Server-E50914?logo=netflix&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.9%2B-C71A36?logo=apachemaven&logoColor=white)
![JaCoCo](https://img.shields.io/badge/JaCoCo-Coverage-success)
![Codecov](https://img.shields.io/badge/Codecov-enabled-F01F7A?logo=codecov&logoColor=white)

[PT-BR](README.md) | [EN](README.en.md)

Servidor de descoberta de servicos baseado em Eureka para o ecossistema de microservicos de votacao.

## Visao geral

- Projeto: `discovery`
- Porta padrao: `8761`
- Java: `17`
- Spring Boot: `3.5.4`
- Spring Cloud: `2025.0.0`

## Tecnologias

- Spring Boot
- Eureka Server (Netflix)
- Maven
- JaCoCo
- Checkstyle
- PMD
- SpotBugs

## Requisitos

- JDK 17
- Maven 3.9+ (ou uso do wrapper `mvnw`)

## Configuracao

Arquivo principal: `src/main/resources/application.properties`

```properties
server.port=8761
spring.application.name=discovery
eureka.client.registerWithEureka=false
eureka.client.fetchRegistry=false
eureka.instance.hostname=localhost
```

## Executar localmente

### Windows (PowerShell)

```powershell
.\mvnw spring-boot:run
```

### Linux/macOS

```bash
./mvnw spring-boot:run
```

## Build e testes

```bash
./mvnw clean package
```

## Qualidade de codigo

```bash
./mvnw checkstyle:check
./mvnw pmd:check
./mvnw spotbugs:check
```

Observacao: no workflow atual, o `spotless:check` esta comentado em CI para este modulo.

## Cobertura de testes

```bash
./mvnw jacoco:report
```

Relatorio gerado em:

- `target/site/jacoco/index.html`

## Pipeline CI

Workflow principal:

- `.github/workflows/workflow-backend-discovery.yml`

Etapas principais:

- Lint/qualidade: Checkstyle, PMD, SpotBugs
- Testes + JaCoCo
- Upload para Codecov
- Build de artefato (`target/*.jar`)

## Dashboard Eureka

- URL: `http://localhost:8761/`

Com o discovery ativo, os demais servicos podem se registrar e ser descobertos dinamicamente pelo gateway.

## Licenca

Uso interno para fins de estudo/desafio.
