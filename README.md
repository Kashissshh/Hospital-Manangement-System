# Hospital-Manangement-System

An enterprise-grade, distributed **Hospital Management System** built on **Spring Boot 3** and **Spring Cloud**. The system utilizes a microservices architecture to manage patient profiles, doctor availability schedules, appointment booking, medical histories, automated email notifications, and centralized JWT-based authentication.

---

## 📐 High-Level System Architecture

```
                                 +-------------------------+
                                 |  Eureka Service Registry| 
                                 +------------+------------+
                                              |
                        Registers & Discovers | Microservices
                                              v
+------------+    HTTP Request    +------------------------+
| Client App | -----------------> |       API Gateway      | (Centralized JWT Authorization)
+------------+                    +-----------+------------+
                                              |
      +--------------------+------------------+-------------------+--------------------+
      | Routing            | Routing          | Routing           | Routing            | Routing
      v                    v                  v                   v                    v
+-----------+        +-----------+      +-----------+       +-----------+        +--------------------+
|   Auth    |        |  Patient  |      |  Doctor   |       |Appointment|        |  Medical History   |
|  Service  |        |  Service  |      |  Service  |       |  Service  |        |      Service       |
+-----------+        +-----+-----+      +-----+-----+       +-----+-----+        +---------+----------+
                           |                  ^                   |                        |
                           | OpenFeign        | OpenFeign         | OpenFeign              | OpenFeign
                           +------------------+-------------------+------------------------+
                                              |
                                              v
                                   +--------------------+
                                   |Notification Service| (JavaMailSender Email Dispatch)
                                   +--------------------+
```

---

## 🧰 Tech Stack & Tools

* **Core Framework**: Java 17+, Spring Boot 3.x
* **Service Discovery**: Spring Cloud Netflix Eureka Server
* **API Gateway**: Spring Cloud Gateway (Custom JWT Filter & Dynamic Route Discovery)
* **Authentication & Security**: Spring Security, JWT 
* **Inter-Service Communication**: OpenFeign Clients
* **Data & Persistence**: Spring Data JPA, Hibernate, MySQL ,JPA
* **Notification System**: Spring Boot Starter Mail (`JavaMailSender`)
* **Utilities**: Lombok, Jackson JSON, Spring Boot Actuator
