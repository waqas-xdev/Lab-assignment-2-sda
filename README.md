# Lab-assignment-2-sda
# Software Problems and Solutions Report

This repository documents common architectural problems encountered in software development and their corresponding solutions. It focuses on key challenges like inadequate modularization, lack of proper layering, insufficient error handling, monolithic systems with slow release cycles, and data consistency across distributed databases. Each problem is paired with its respective solution, detailing the design patterns, principles, and technologies used to overcome them.

## Table of Contents

1. [Inadequate Modularization](#inadequate-modularization)
2. [Lack of Proper Layering (Separation of Concerns)](#lack-of-proper-layering-separation-of-concerns)
3. [Insufficient Error Handling Mechanisms](#insufficient-error-handling-mechanisms)
4. [Monolithic Systems with Slow Release Cycles](#monolithic-systems-with-slow-release-cycles)
5. [Data Consistency Across Distributed Databases](#data-consistency-across-distributed-databases)

## Introduction

In modern software systems, particularly distributed systems, ensuring reliability and resilience is critical. The report highlights five common software architectural problems, explains the challenges they present, and outlines the solutions implemented to address them. Additionally, it explores the key principles applied to ensure better software maintainability, scalability, and robustness.

## Problems and Solutions

### 1. Inadequate Modularization

- **Problem**: In monolithic systems, code becomes highly tangled, making maintenance difficult. Adding new features can unintentionally affect other parts of the system due to tight coupling.
- **Solution**: The system was refactored into small, independent modules with minimal dependencies. Microservices architecture or modular design patterns were implemented to reduce coupling, simplify scalability, and enhance maintainability.
- **Principle Used**: Single Responsibility Principle (SRP)

### 2. Lack of Proper Layering (Separation of Concerns)

- **Problem**: Poorly structured systems often intertwine presentation logic, business logic, and data access, making it difficult to scale or maintain.
- **Solution**: The architecture was refactored into a layered design, such as MVC (Model-View-Controller), where each layer had a distinct responsibility. This improved maintainability, scalability, and independent management of different system parts.
- **Principle Used**: Separation of Concerns (SoC)

### 3. Insufficient Error Handling Mechanisms

- **Problem**: Inadequate error handling leads to system crashes, especially in distributed systems where failures cascade through multiple components. Lack of centralized logging complicates debugging.
- **Solution**: Specific exceptions were implemented, and centralized logging and monitoring were introduced. Fault-tolerant design patterns, such as the Circuit Breaker, were utilized to ensure the system could recover gracefully from failures without affecting the entire system.
- **Principle Used**: Fail Fast — Detect and handle errors early to prevent system-wide failures.

### 4. Monolithic Systems with Slow Release Cycles

- **Problem**: Large monolithic systems result in slow release cycles, where adding new features or fixing bugs takes considerable time, delaying product delivery.
- **Solution**: The system was migrated to a microservices architecture, breaking it into small, independent services that allowed for faster release cycles, scalability, and individual service updates.
- **Principle Used**: Autonomy of Components — Independent services that can be deployed and scaled separately.

### 5. Data Consistency Across Distributed Databases

- **Problem**: In distributed systems with multiple databases, ensuring data consistency becomes difficult. Changes in one database may not immediately reflect in others, leading to data corruption or outdated information.
- **Solution**: Strong consistency was implemented using the CAP theorem, event sourcing, CQRS (Command Query Responsibility Segregation), and techniques like two-phase commit and atomic transactions. For high-availability systems, hybrid approaches were used to combine ACID-compliant and eventually consistent databases.
- **Principle Used**: Eventual Consistency — Allows temporary inconsistency for improved availability and partition tolerance.

## Error Handling and Circuit Breaker Implementation

### **Error Handling Solution:**

In distributed systems, where failures can cascade across components, error handling plays a crucial role in ensuring system reliability. By implementing robust error handling and fault tolerance mechanisms like the Circuit Breaker pattern, the system can handle failures without causing significant disruptions.

- **Before**: The system failed silently or displayed generic error messages, making it difficult for developers to troubleshoot issues. This led to delays in issue resolution and poor user experiences.
- **Solution**: 
    - **Specific Exceptions**: Errors were categorized into distinct types like `PaymentGatewayException`, `UserNotFoundException`, and `PaymentProcessingException`.
    - **Meaningful Logging**: Centralized logging was integrated to capture error details, which helped developers trace and fix issues more efficiently.
    - **User-Friendly Messages**: Instead of generic error messages, users now receive clear and actionable feedback (e.g., "Unable to process payment, please try again later").
- **Principle Used**: Robustness Principle (Fail-Fast) — Ensuring systems fail gracefully with enough information to aid in debugging and recovery.

### **Circuit Breaker Pattern:**

The Circuit Breaker pattern prevents the system from repeatedly calling failing services, allowing the system to recover and continue functioning even when part of it fails. This is achieved by monitoring the health of external services and temporarily halting requests to failing services.

## Setup and Usage

### Prerequisites

- Java 8 or later
- Maven for dependency management
- Resilience4j library for Circuit Breaker pattern implementation

### Installation

1. Clone the repository:

``bash
git clone https://github.com/yourusername/software-problems-solutions.git
cd software-problems-solutions


Install dependencies:
bash
Copy code
mvn install
Add Resilience4j to your pom.xml:
xml
Copy code
<dependency>
    <groupId>io.github.resilience4j</groupId>
    <artifactId>resilience4j-circuitbreaker</artifactId>
    <version>1.7.0</version>
</dependency>
Running the Application
After setting up the dependencies, you can run the system to observe error handling, logging, and the Circuit Breaker in action. For more details on how to use the system, refer to the src/main/java directory for code implementations.

Contributing
Fork the repository.
Create a new branch (git checkout -b feature-xyz).
Commit your changes (git commit -am 'Add feature xyz').
Push to the branch (git push origin feature-xyz).
Create a new pull request.
License
This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgments
Resilience4j for providing the Circuit Breaker library.
Software architects and developers for proposing best practices and principles.


