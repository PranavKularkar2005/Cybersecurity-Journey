# 🕸️ TryHackMe Room: HTTP in Detail

This repository tracks my structured technical notes, communication flow maps, status code breakdowns, and structural headers for the **HTTP in Detail** room under the *How The Web Works* module. Developing a granular understanding of web request and response headers is crucial for an L1 SOC Analyst to pinpoint web application vulnerabilities, analyze malicious payloads, and spot command-and-control (C2) traffic patterns.

---

## 🔒 Task 1: What is HTTP(S)?

**HTTP** (HyperText Transfer Protocol) was developed by Tim Berners-Lee and his team between 1989 and 1991. It establishes the rigid set of syntactic rules used by web clients (browsers) to communicate with remote web servers to transmit webpage assets (including HTML files, raw images, streaming videos, and structural scripts).

### The Essential Shift to HTTPS:
* **The Vulnerability of HTTP:** Clear-text HTTP transmits data without any native encryption. If an adversary positions themselves inline along a communication boundary, they can read sensitive data (like credentials or financial inputs) using simple packet sniffer software.
* **The Secure Layer (HTTPS):** HyperText Transfer Protocol Secure wraps the standard HTTP payload inside an encrypted channel (**SSL/TLS**). This ensures data confidentiality, prevents unauthorized traffic tampering, and provides clear cryptographic validation that the client is interacting with a legitimate destination server instead of a rogue imposter.

### 🏆 Task 1 Knowledge Verification
* What does HTTP stand for? $\rightarrow$ `HyperText Transfer Protocol`
* What does the S in HTTPS stand for? $\rightarrow$ `secure`
* **Interactive Challenge Flag:** `THM{INVALID_HTTP_CERT}`

---

## 🔗 Task 2: Requests And Responses

When a user triggers an interaction on a website, the browser formats a structured request targeting a specific server asset. The location mapping for these assets is defined by a **URL** (Uniform Resource Locator).

### Anatomy of a Uniform Resource Locator (URL):


* **Scheme:** Instructs the local operating system which network protocol to invoke to parse the resource (e.g., `http://`, `https://`, or `ftp://`).
* **User Info:** Optional field containing inline authentication parameters (`username:password`) required to access protected folder pools.
* **Host:** The target domain name string or literal logical IP address of the remote web server hosting the assets.
* **Port:** The specific connection endpoint channel mapped on the server host (defaults to port `80` for unencrypted HTTP and port `443` for secure HTTPS).
* **Path:** The explicit directory path indicating where the targeted file or script sits inside the server's storage layout.
* **Query String:** Extra data variables passed directly down to the server-side backend engine, beginning with a question mark (`?`).
* **Fragment:** An internal coordinate indicator marked with a hash tag (`#`) to instantly snap the browser viewport down to a specific anchor section of the rendered page.

---

### Deep Dissection of an HTTP Transaction:

#### 🛫 1. The Raw HTTP Request Layout
Web requests can be initialized at a bare minimum using a single plain-text line format: `GET / HTTP/1.1`. A realistic corporate browser transaction layout uses the following format:

```http
GET /index.html HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: [https://tryhackme.com/](https://tryhackme.com/)
