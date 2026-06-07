# 🌐 Client-Server Basics

## 📖 Overview

This repository contains my notes and walkthrough for the **Client-Server Basics** room from the **Computer Fundamentals** module in TryHackMe.

The room introduces the Client-Server architecture, networking fundamentals, DNS, protocols, ports, and HTTP communication. A practical lab demonstrates how web browsers communicate with web servers using HTTP requests and responses.

---

# 🎯 Learning Objectives

After completing this room, I learned:

- The Client-Server model
- How requests and responses work
- The purpose of communication protocols
- How ports identify services
- How DNS resolves domain names
- HTTP and HTTPS fundamentals
- How browsers communicate with web servers
- How to inspect HTTP traffic using browser developer tools

---

# 📝 Task 1: Introduction

Modern computer systems communicate with each other through networks. Early networks such as ARPANET, CYCLADES, NPL, and NSFNET eventually evolved into the modern Internet.

This room introduces several important networking concepts:

- Client
- Server
- Protocol
- Port
- DNS
- Network

### Key Takeaway

The Internet is built upon interconnected systems that communicate using standardized protocols and services.

---

# 📝 Task 2: Pizza Delivery Analogy

TryHackMe explains networking concepts using a pizza delivery example.

## Client and Server

### Client

A client initiates communication and requests a service.

**Examples:**
- Web Browser
- Mobile Application
- Email Client

### Server

A server provides services and responds to requests.

**Examples:**
- Web Server
- Database Server
- Mail Server

> The client always initiates communication.

---

## Request and Response

Communication follows a request-response model.

### Request

A message sent by the client requesting a resource.

```http
GET /index.html HTTP/1.1
```

### Response

A message sent by the server after processing the request.

```text
200 OK
```

Responses may contain:

- Web pages
- Images
- Files
- Error messages

---

## Protocol

A protocol is a set of rules that define how communication occurs between systems.

Protocols define:

- Commands
- Syntax
- Message format
- Communication order
- Expected responses

**Examples:**

- HTTP
- HTTPS
- FTP
- SMTP
- DNS

---

## Port

A port identifies a specific service running on a device.

| Port | Service |
|--------|----------|
| 80 | HTTP |
| 443 | HTTPS |
| 21 | FTP |
| 22 | SSH |
| 25 | SMTP |

A single server can provide multiple services simultaneously using different ports.

---

## DNS (Domain Name System)

DNS translates domain names into IP addresses.

```text
tryhackme.com
↓
IP Address
```

Without DNS, users would need to remember IP addresses instead of website names.

---

# 📝 Task 3: Web Communication in Practice

This task demonstrated how web browsers communicate with web servers using HTTP.

## HTTP and HTTPS

### HTTP

**HyperText Transfer Protocol**

Used to transfer web content between clients and servers.

### HTTPS

**HyperText Transfer Protocol Secure**

Provides encrypted communication between clients and servers.

---

## Stateless Communication

HTTP is stateless.

This means:

- Each request is independent.
- The server does not automatically remember previous requests.

To maintain user sessions, websites use:

- Cookies
- Session IDs
- Authentication Tokens

---

## Common HTTP Methods

| Method | Purpose |
|----------|----------|
| GET | Retrieve data |
| POST | Submit data |
| PUT | Update data |
| DELETE | Remove data |
| PATCH | Modify data |
| HEAD | Retrieve headers |
| OPTIONS | Show supported methods |
| CONNECT | Create communication tunnel |
| TRACE | Diagnostic requests |

---

## Practical Lab Exercise

### Objective

Observe and analyze real HTTP communication between a browser and a web server.

### Tools Used

- TryHackMe Lab Machine
- Firefox Browser
- Firefox Developer Tools
- Network Tab

### Procedure

1. Started the Lab Machine.
2. Opened the HTTP Demo Website.
3. Pressed **F12** to launch Developer Tools.
4. Opened the **Network** tab.
5. Reloaded the webpage.
6. Observed multiple GET requests.
7. Selected the first request.
8. Examined request and response details.

---

## GET Request Analysis

Example:

```http
GET /index.html HTTP/1.1
```

The browser requests a resource from the server.

---

## Request Information Observed

| Field | Description |
|---------|------------|
| Scheme | Protocol used |
| Host | Website hostname |
| Filename | Requested resource |
| Address | Server IP address |
| Method | HTTP Method |

### Example Values

| Field | Value |
|---------|--------|
| Scheme | HTTP |
| Host | httpdemo.local:8080 |
| Filename | index.html |
| Address | 127.0.0.1 |
| Method | GET |

---

## Response Analysis

The server returned:

### Response Header

Contains metadata such as:

- Status Code
- Content Length
- Content Type
- Server Information

### Response Body

Contains:

- HTML
- CSS
- JavaScript
- Images

---

## Status Code Observed

```text
200 OK
```

Meaning:

- Request successful
- Resource found
- Content returned

---

## Key Observation

A single webpage generates multiple requests automatically.

Examples:

- index.html
- style.css
- script.js
- favicon.ico

The browser downloads all required resources before rendering the webpage.

---

## Questions & Answers

### What would be the host in the following URL?

```text
https://www.iamlearning.thm/contact
```

**Answer:**

```text
www.iamlearning.thm
```

### What would be the scheme in the following URL?

```text
https://www.iamlearning.thm/contact
```

**Answer:**

```text
https
```

---

# 📝 Task 4: Conclusion

This room demonstrated how services are provided over networks using the Client-Server model.

The room also introduced practical HTTP communication and showed how browsers interact with web servers.

### Concepts Covered

- Client-Server Architecture
- DNS
- Ports
- Protocols
- HTTP
- Requests and Responses
- Browser Developer Tools

---

# 🔑 Key Takeaways

- Clients request services.
- Servers provide services.
- Protocols define communication rules.
- Ports identify specific services.
- DNS resolves names into IP addresses.
- HTTP powers web communication.
- HTTPS secures communication through encryption.
- Developer Tools help analyze web traffic.

---

# 🛠 Skills Gained

- Client-Server Fundamentals
- Networking Basics
- DNS Concepts
- HTTP Fundamentals
- Web Communication Analysis
- Browser Developer Tools
- Request and Response Inspection
- Cybersecurity Foundations

---

# 📚 Platform

- TryHackMe
- Learning Path: Pre-Security
- Module: Computer Fundamentals
- Room: Client-Server Basics

---

# 🚀 Status

✅ Completed Successfully
