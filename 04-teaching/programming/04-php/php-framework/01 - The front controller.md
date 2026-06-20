---
type: lesson
tags:
  - php
created: 2026-06-11 16:58
---
In the **front controller pattern**, all incoming requests are routed through a single entry point—typically an `index.php` file—which then acts as a central hub for the application (1:25-1:35). 

Delegation works through these key steps:

* **Centralized Request Handling:** Instead of the browser hitting specific, independent files like `home.php` or `list.php`, the server directs everything to the **front controller** (1:30, 4:20).
* **Input Inspection:** The controller examines the request, often by looking at the **query string** (e.g., `?page=home`) to determine what the user is trying to access (3:45).
* **Task Routing:** Based on the input, the controller decides which specific script or logic to execute. In the provided example, the controller uses a `require` statement to pull in the content from the appropriate file (3:52, 4:28).
* **Delegation:** By acting as a traffic cop, the front controller allows common tasks—such as database connections, authentication, and error handling—to be performed in one place before delegating the specific content rendering to the appropriate sub-script (1:05-1:40).

While the example shown is a basic implementation (4:44), this pattern provides a foundation for more advanced **routing systems** used in frameworks like *Laravel* or *Symfony* (5:15-5:20).