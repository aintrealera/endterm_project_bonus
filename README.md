# Library Management System API

## 1. Description
This is a Spring Boot REST API for a Library System. It allows users to manage books (Create, Read, Delete) and demonstrates the usage of Design Patterns and SOLID principles.

## 2. Tech Stack
* **Java 17**
* **Spring Boot 3.4.x**
* **PostgreSQL**
* **Maven**

---

## 3. Design Patterns Used
I implemented 3 patterns as required:

### 1. Singleton (`LibraryLogger`)
* **What it does:** Creates one global instance for logging.
* **Where to find:** `src/main/java/.../pattern/LibraryLogger.java`
* **Usage:** Logs every GET request in the Console.

### 2. Factory (`BookFactory`)
* **What it does:** Creates different types of books (Digital/Physical) based on a simple string parameter.
* **Where to find:** `src/main/java/.../pattern/BookFactory.java`

### 3. Builder (`Book.Builder`)
* **What it does:** Helps to create `Book` objects cleanly without huge constructors.
* **Where to find:** Inside `Book.java` model.

---

## 4. API Endpoints
Base URL: `http://localhost:8080/api/books`

| Method | URL | Description |
| :--- | :--- | :--- |
| **GET** | `/api/books` | Get list of all books |
| **POST** | `/api/books` | Create a book (JSON body) |
| **POST** | `/api/books/quick` | Create via Factory (Params: `title`, `type`) |
| **DELETE** | `/api/books/{id}` | Delete book by ID |

---

## 5. How to Run

1. **Database:**
   * Make sure PostgreSQL is running.
   * Create a database named `library_db`.

2. **Configuration:**
   * Open `src/main/resources/application.properties`.
   * Check your username and password.

3. **Run:**
   * Run `LibrarySystemApplication.java` in IntelliJ IDEA.

---

## 6. Screenshots
Please check the `screenshots/` folder for proof of work:

* **1. GET Request:** `get_all_books.png` - Shows the list of books returning 200 OK.
* **2. POST (Builder):** `post_create_builder.png` - Creating a standard book with JSON body.
* **3. POST (Factory):** `post_create_factory.png` - Creating a book via query params (Factory pattern).
* **4. DELETE Request:** `delete_book.png` - Deleting a book by ID.
* **5. Database:** `database_view.png` - View of the `books` table in PostgreSQL.
* **6. UML:** `uml_diagram.png` - Project architecture diagram.
