# 🌐 TryHackMe Room: How Websites Work

This repository contains my structured technical notes, client-server transaction flow maps, source-code analysis examples, and entry-level vulnerability notes for the **How Websites Work** room under the *How The Web Works* module. Developing a firm grasp of front-end structure and client-side logic is essential for web application security assessments, source-code audits, and identifying application injection vectors.

---

## 🏛️ Task 1: How Websites Work

Websites are hosted on web servers, which are simply specialized computers dedicated to listening for and handling incoming user requests over network sockets. When you visit a domain path via a browser, a fundamental **Request-Response** cycle occurs over the internet.

### The Two Major Web Application Components:
1. **Front End (Client-Side):** The user-facing code executed and rendered directly inside your browser window (e.g., Safari, Firefox, or Google Chrome). It handles how the site looks and presents information visually.
2. **Back End (Server-Side):** The remote server application logic that processes incoming requests, talks to internal database pools, and delivers the corresponding response data blocks back to the client.

### 🏆 Task 1 Knowledge Verification
* What term best describes the component of a web application rendered by your browser? $\rightarrow$ `Front End`

---

## 🏗️ Task 2: HTML (HyperText Markup Language)

**HTML** is the core language websites are written in. Elements (also known as tags) serve as the fundamental building blocks of HTML pages, instructing the browser's layout engine exactly how to structure and display text, links, and media assets.

### Anatomy of a Standard HTML Structure:
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    <h1>Example Heading</h1>
    <p>Example paragraph..</p>
  </body>
</html>
Essential Tag Meanings:<!DOCTYPE html>: Notifies the browser engine that the document is a modern HTML5 file to ensure consistent rendering across different modern web browsers.<html>: The root container element enclosing all other operational tags within the document structure.<head>: Stores key configuration data and background elements about the page that are not visible on the screen (such as the page title metadata block).<body>: Houses the structural content layout that is visible to the end-user inside the browser viewport.<h1>: Defines a major structural heading banner using the largest default font thickness.<p>: Formats text elements into a standard paragraph structure.<img>: Integrates graphic images into the document using dedicated locator path strings.Understanding Structural Attributes:Tags utilize internal attributes to inject specific configuration parameters or style indicators onto an explicit element:Class (class="..."): Groups similar components together to apply unified styling templates (e.g., coloring specific elements blue).Source (src="..."): Pinpoints the precise file path directory of an asset, such as an image location link (<img src="img/cat-1.jpg">).Identifier (id="..."): Assigns a completely unique name tag to a single element. IDs are unique across a single document and are used to help JavaScript target specific elements dynamically.🏆 Task 2 Practical Lab AnswersFix the broken cat image on the lab editor website $\rightarrow$ No answer neededWhat is the hidden text revealed on the cat image once fixed? $\rightarrow$ HTMLHEROAdd a dog image to the page on line 11 using <img src='img/dog-1.png'>. What is the text embedded in the dog image? $\rightarrow$ DOGHTML🎨 Task 3: JavaScript (JS)While HTML dictates a site's structure, JavaScript (JS) is a powerful dynamic client-side programming language that enables static pages to become interactive and responsive in real-time.Key Capabilities of JavaScript:Modifies page content, attributes, and formatting dynamically without forcing a complete page refresh.Monitors browser actions, triggering specific styling changes or functional blocks when user events occur (e.g., clicks, mouse hovers, or key presses).Manages complex animations, data validation checkers, and modern application functions.Implementation Methods:JavaScript scripts can be typed directly between local HTML <script> tags, or loaded from a separate asset file using the source attribute pointer:
<script src="/location/of/javascript_file.js"></script>
// Locates a target element by its unique ID and swaps out its inner text dynamically
document.getElementById("demo").innerHTML = "Hack the Planet";

// Creates an interactive button that changes a page block instantly when clicked
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>Click Me!</button>

🔑 Task 4: Sensitive Data Exposure
Sensitive Data Exposure happens when developers accidentally leave sensitive clear-text records, test configurations, or hidden pathways visible to the public. These mistakes are commonly found inside a web application's client-side front-end source code.

Core Attack Vectors & Inspection Rules:
Source Code Comments: Developers often use inline HTML comments (``) to leave notes for themselves. Adversaries audit these fields to locate forgotten test accounts, hardcoded administrative keys, or legacy administrative URLs.

Hardcoded Credentials: Storing unencrypted staging profiles or backend database connection passwords directly inside static HTML blocks or custom JavaScript files.

The First Rule of Web App Auditing: When assessing any web application interface for flaws, your initial step should always be to right-click the page and select "View Page Source" to inspect exactly what details the server is pushing down to the client device.

<form method="post" id="form" autocomplete="off">
  <input class="input-text" type="text" name="username" placeholder="Username..">
  <input class="input-text" type="password" name="password" placeholder="Password..">
  <button class="login">Login</button>
  </form>

🏆 Task 4 Practical Lab AnswersNavigate to the target web application link and inspect its source code. What is the hidden password comment string? $\rightarrow$ testpasswd🪡 Task 5: HTML InjectionHTML Injection is a web security vulnerability that occurs when a web application takes unfiltered or un-sanitized user input and reflects it directly onto the webpage layout. If a site fails to sanitize inputs, an attacker can submit raw HTML or JavaScript code, forcing the browser to render it as trusted code.

1. User types un-sanitized data into an input box (e.g., submitting an active hyperlink string).
2. The browser accepts the input block and processes it through a JavaScript function.
3. Because no validation runs, the malicious code executes on the page, changing the site's layout.

1. User types un-sanitized data into an input box (e.g., submitting an active hyperlink string).
2. The browser accepts the input block and processes it through a JavaScript function.
3. Because no validation runs, the malicious code executes on the page, changing the site's layout.
