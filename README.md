# Spring Cloud Config Server

## Student Information
* **Name:** Lahiru Mudith
* **Student Number:** CMS-ST-2026
* **GCP Project ID:** `cms-cloud-architecture`

---

## Service Overview
The **Config Server** acts as the central property manager for the entire Clinic Management System platform. Instead of keeping properties inside individual project repositories, configurations are managed in a single directory and served over REST to all registering microservices.

* **Default Port:** `8888`
* **Technology:** Spring Cloud Config Server.
* **Target Environment:** OpenJDK 25, Spring Boot 4.1.1, Spring Cloud 2025.1.3.

---

## Configuration Source (Native File System)
The configurations are fetched from the local classpath in the directory:
[`src/main/resources/configurations`](file:///C:/Users/Lahiru%20Mudith/Documents/Study/IJSE/4th%20Sem/Enterprise%20Cloud%20Architectur/Projects/Clinic-Management-System/cms-platform/config-server/src/main/resources/configurations/)

It hosts the following YAML property sheets:
* **`application.yaml`:** Shared configurations (common Eureka client registration properties).
* **`platform/api-gateway.yaml`:** CORS rules and route bindings.
* **`platform/service-registry.yaml`:** Eureka port and registry properties.
* **`services/service-patient.yaml`:** PostgreSQL credentials, AOP toggles, and GCP Cloud Storage credentials.
* **`services/service-doctor.yaml`:** MongoDB connection strings.
* **`services/service-appointment.yaml`:** MySQL connection strings.

---

## REST Endpoints for Retrieving Configs

Registering clients call the server using standard Spring formats:
* `GET /{application}/{profile}`
* `GET /{application}/{profile}/{label}`

### Example Verification Curl:
```bash
curl http://localhost:8888/api-gateway/default
```

---

## Build and Run

### Build Command:
```bash
mvn clean package -DskipTests
```

### Execution Command:
```bash
java -jar target/Config-Server-1.0.0.jar
```
