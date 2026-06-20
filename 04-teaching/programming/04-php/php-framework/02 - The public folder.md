---
type: lesson
tags:
  - php
created: 2026-06-11 17:01
---
# 02 - The public folder

## This video explains the security and organizational benefits of using a **'public' folder** in PHP frameworks, a standard practice in frameworks like *Laravel* and *Symfony* (0:00-0:11).

**Key Takeaways:**

* **The Security Problem:** Storing all project files in a single web-accessible directory allows users to bypass the front controller and potentially access sensitive files like configuration or settings directly via a browser (0:11-1:28).
* **The 'public' Folder Solution:** By creating a `public` folder and moving the front controller (`index.php`) and static assets (like CSS and JavaScript) there, you limit what is directly accessible. You must then configure your web server (such as the PHP development server or *Apache*) to set this folder as the **document root** (1:28-4:52).
* **Preventing Code Exposure:** Placing PHP source code outside the web root protects your logic from being exposed if the server is misconfigured and fails to execute PHP scripts, effectively downloading the raw code instead (4:52-6:31).
* **Bootstrap Files:** To keep the front controller minimal and secure, the video demonstrates moving application logic into a `bootstrap.php` file located within a `src` (source) folder outside the public directory (6:31-8:37).

In summary, the `public` folder acts as a gatekeeper, separating private source code from public-facing assets, which significantly enhances the security and professional structure of a PHP application (8:37-8:55).

## Related Notes
- [[01 - The front controller]]
- [[03 - HTTP messages]]
