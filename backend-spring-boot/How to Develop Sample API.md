# 🚀 Spring Boot Roadmap

Since your Spring Boot application is created successfully, the next step is **not Docker or AWS yet**. We will build it step by step.

---

# 📌 1. Create your first REST API

Create a simple controller:

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello Spring Boot";
    }
}
```

---

# ▶ Run and Test API

Start your Spring Boot application and open this URL:

👉 [Test API](http://localhost:8080/hello)

You will see output:

```
Hello Spring Boot
```

---

# 🧠 What you learned here

- `@RestController` → Makes class a REST API controller  
- `@GetMapping("/hello")` → Maps HTTP GET request  
- Spring Boot automatically handles request → response flow  

---

# 🔄 Request Flow (Internal Working)

```text
Browser / Postman
        ↓
DispatcherServlet
        ↓
HelloController
        ↓
Response returned
```

---

# 📌 Important Concepts

## REST API
Used for communication between client and server.

## Controller
Handles incoming HTTP requests.

## Annotations

- `@RestController` → REST API class  
- `@GetMapping` → GET endpoint  

---


# 🚀 What I Did After Creating HelloController 

---

## 3. Understood DispatcherServlet Flow

I learned how request flows internally:

```
Browser / Postman
      ↓
DispatcherServlet
      ↓
HandlerMapping
      ↓
HelloController
      ↓
Response returned
```

---

## 4. Improved API Structure using /api prefix to create sample employee api

Instead of:

```
/employee
```

I started using:

```
/api/employee
```

Using:

```java
@RequestMapping("/api")
```

---

## 5. Learned Java Object → JSON Conversion

Spring Boot automatically converts Java objects to JSON using Jackson.

## 📂 Creating Controller Package and EmployeeController

## 1. Create a Controller Directory

Inside the Spring Boot project structure, I created a new package:

```
controller/
```

This package is used to keep all REST API controllers.

---

## 2. Create EmployeeController Class

Inside the `controller` package, I created:

```java
@RestController

@RequestMapping("/api")
public class EmployeeController {
    @GetMapping("/employee")
    public Employee[] getEmployees(){
        Employee employee1 = Employee.builder()
                        .id(1)
                        .name("Naveen")
                        .salary(10000.00).build();
        Employee employee2 = Employee.builder()
                .id(1)
                .name("Naveen")
                .salary(10000.00).build();

        return new Employee[] {employee2, employee1};
    }
}
```

### Output:
```json
{
  "id": 1,
  "name": "Naveen",
  "salary": 10000
}
```

---

## 6. Learned Why Constructors Are Not Scalable

If an object has many fields (50–100), constructors become hard to manage.

So I learned alternatives:

- Getters & Setters
- Lombok (@Data)
- Builder Pattern

---

## 7. Used Lombok for Cleaner Code

Example:

```java
@Data
@Builder
public class Employee {
    private int id;
    private String name;
    private String department;
    private double salary;
}
```


## 🧠 Key Learnings So Far

- Spring Boot uses DispatcherServlet for request routing
- REST APIs return JSON automatically
- `/api` is best practice for API design
- Java objects are converted to JSON using Jackson
- Lombok reduces boilerplate code