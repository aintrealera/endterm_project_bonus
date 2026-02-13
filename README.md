# Library Management System with In-Memory Cache

##  Project Overview

This project is a simple **Library Management System** implemented as a **Spring Boot REST application**.  
It demonstrates the use of **layered architecture**, **creational design patterns**, and **component cohesion principles**.

As a bonus feature, a **simple in-memory caching layer** was added to improve performance for frequently accessed data.

---

##  Architecture

The project follows a **layered architecture**:

- **Controller layer** – handles HTTP requests
- **Service layer** – contains business logic
- **Repository layer** – interacts with the database
- **Model layer** – represents domain entities
- **Cache layer** – manages cached data
- **Pattern layer** – contains design pattern implementations

This separation improves maintainability and follows the **Separation of Concerns** principle.

---

##  Design Patterns Used

### Singleton
- Used in `LibraryLogger` to ensure only one logger instance exists.
- Used in `BookCache` to manage a single cache instance across the application.

### Factory Method
- Implemented in `BookFactory`.
- Responsible for creating `Book` objects based on their type.
- Keeps object creation logic separate from business logic.

### Builder
- Implemented as a static inner class in `Book`.
- Allows step-by-step creation of complex objects.
- Improves readability and avoids large constructors.

---

##  In-Memory Caching Layer (Bonus Task)

### Objective
Improve application performance by caching frequently requested data in memory.

### Implementation Details
- A simple **in-memory cache** is implemented using a Singleton class `BookCache`.
- The cache stores the result of the `getAllBooks()` method.
- Cached data is returned on repeated calls instead of querying the database again.
- The cache is **automatically invalidated** after `save` or `delete` operations.

### Why Singleton?
Only one cache instance should exist to ensure consistent cached data across the application.

---

##  Cache Invalidation Strategy

- **Read operation (`getAllBooks`)**
  - If cached data exists → return it
  - If not → fetch from database and store in cache

- **Write operations (`save`, `delete`)**
  - Cache is cleared to prevent stale data

---

## 📐 SOLID & Component Principles

- **Single Responsibility Principle (SRP)**  
  Each class has a single responsibility (controller, service, cache, repository).

- **Reuse/Release Equivalence Principle (REP)**  
  Related classes are grouped and reused together.

- **Common Closure Principle (CCP)**  
  Classes that change together are grouped logically.

- **Common Reuse Principle (CRP)**  
  Controllers depend only on services, not on repositories or cache directly.

---

##  Technologies Used

- Java
- Spring Boot
- Spring Data JPA
- REST API
- In-Memory Caching
- Maven

---

##  Summary

This project demonstrates:
- Clean layered architecture
- Proper use of creational design patterns
- Application of component cohesion principles
- Performance optimization using a simple in-memory cache

The caching mechanism enhances performance while preserving architectural integrity and SOLID principles.
