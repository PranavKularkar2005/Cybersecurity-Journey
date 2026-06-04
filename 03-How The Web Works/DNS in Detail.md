# 🔍 TryHackMe Room: DNS in Detail

This repository contains my structured technical notes, domain hierarchical maps, and configuration lookups for the **DNS in Detail** room under the *How The Web Works* module. Developing a deep operational understanding of the Domain Name System is vital for identifying phishing vectors, diagnosing malicious subdomains, and detecting DNS tunneling techniques.

---

## 🛠️ Task 1: What is DNS?

The **Domain Name System (DNS)** acts as the universal phonebook of the internet. It provides a seamless mechanism to translate human-readable website URLs into the machine-readable logical strings known as **IP Addresses**.

### The Core Premise:
* **The Problem:** Computers communicate natively via numeric strings across a 32-bit layout (e.g., `104.26.10.229`). Expecting users to memorize complex numeric indicators for every destination across the web is completely unrealistic.
* **The Solution:** DNS resolves friendly strings like `tryhackme.com` to its corresponding backend server locator. Instead of typing raw destination strings, the system references local or remote name records to handle routing behind the scenes.

### 🏆 Task 1 Knowledge Verification
* What does DNS stand for? $\rightarrow$ `Domain Name System`

---

## 🌳 Task 2: Domain Hierarchy

The DNS namespace is structured as an inverted hierarchical tree database managed by international authorities. A complete domain name string is limited to a maximum length of **253 characters total**.

### The 3 Structural Tiers of a Domain:

1. **Top-Level Domain (TLD):** The rightmost element of a domain string. TLDs are split into two primary buckets:
    * *gTLD (Generic Top-Level Domain):* Identifies the primary purpose or sector of the space (e.g., `.com` for commercial use, `.org` for organizations, `.edu` for educational facilities, `.gov` for governments).
    * *ccTLD (Country Code Top-Level Domain):* Identifies explicit geographical regions or distinct nations (e.g., `.co.uk` for the United Kingdom, `.ca` for Canada, `.in` for India).
2. **Second-Level Domain (SLD):** Sits directly to the left of the TLD. It is the unique identifier registered by an individual or business entity. Limited strictly to **63 characters maximum** using characters `a-z`, `0-9`, and hyphens (`-`). It cannot start/end with a hyphen or contain an underscore (`_`).
3. **Subdomain:** Sits on the far-left side of the Second-Level Domain, separated by a period (`.`) to mark specific server sub-divisions or test environments (e.g., `admin` or `store`). It follows the same 63-character limit as the SLD.

### 🏆 Task 2 Knowledge Verification
* What is the maximum length of a subdomain? $\rightarrow$ `63`
* Which of the following characters cannot be used in a subdomain? $\rightarrow$ `_`
* What is the maximum length of a domain name? $\rightarrow$ `253`
* What type of TLD is .co.uk? $\rightarrow$ `ccTLD`

---

## 📋 Task 3: Record Types

DNS databases utilize specific **Record Types** to dictate how distinct lookup queries against a domain name space should be routed and addressed.

### Common DNS Record Matrix:
| Record Type | Core Data Object Mapping Target | Primary Operational Purpose |
| :--- | :--- | :--- |
| **A** | `IPv4 Address` | Maps a host string to a standard 32-bit IPv4 address (e.g., `104.26.10.229`). |
| **AAAA** | `IPv6 Address` | Maps a host string to a modern 128-bit hexadecimal IPv6 address. |
| **CNAME** | `Domain Name` | Canonical Name record. Maps a subdomain alias to another canonical domain string (e.g., routing `store.domain.com` over to a third-party host platform). |
| **MX** | `Mail Server Address` | Mail Exchanger. Points directly to the servers managing incoming email traffic for the domain space. Features an explicit priority flag matrix. |
| **TXT** | `Text Strings` | Free-text field used to store arbitrary descriptions. Extensively used to hold SPF, DKIM, and DMARC parameters to stop email spoofing and prove domain ownership. |

### 🏆 Task 3 Knowledge Verification
* What type of record would be used to advise where to send email? $\rightarrow$ `MX`
* What type of record handles IPv6 addresses? $\rightarrow$ `AAAA`

---

## 🏃 Task 4: Making A Request

When a client queries a domain name, a multi-step lookup request triggers if the value isn't found inside the local system cache registry.

### The 5-Step DNS Resolution Path:
1. **Local Cache Check:** The client machine evaluates its local cache log. If empty, the query hits the **Recursive DNS Server** (typically provided by your local ISP or public relays like Google `8.8.8.8`).
2. **The Root Servers (`.`):** If the Recursive server lacks a cached mapping, it talks to the global root servers. Root servers act as the backbone of the internet, directing the Recursive tool to the authoritative TLD server dealing with the target suffix (e.g., directing a `.com` hit to `.com` TLD infrastructure).
3. **TLD Servers:** The TLD zone server receives the request and returns the location tracking coordinates pointing toward the domain's specific **Authoritative Name Servers**.
4. **Authoritative Server:** This server holds the true master records for the domain. It identifies the target record mapping (like an `A` record match) and returns it cleanly down to the Recursive server.
5. **Lease & Cache (TTL):** The Recursive engine delivers the address back to the initial client and saves a temporary local copy. The length of time this copy stays valid is governed strictly by the record's **TTL (Time to Live)** parameter, measured in seconds.

### 🏆 Task 4 Knowledge Verification
* What field specifies how long a DNS record should be cached for? $\rightarrow$ `TTL`
* What type of DNS Server is usually provided by your ISP? $\rightarrow$ `recursive`
* What type of server holds all the records for a domain? $\rightarrow$ `authoritative`

---

## 💻 Task 5: Practical - Lookups Challenge

This section tracks active interactive diagnostics using the terminal utility `nslookup` against an isolated laboratory name server grid to parse real-time zone file variables.

### Diagnostic Command-Line Trace:
```bash
# 1. Querying Canonical Identity for shop subdomain
user@thm:~$ nslookup --type=CNAME shop.website.thm
Server:     127.0.0.0.53
Address:    127.0.0.0.53#53

Non-authoritative answer:
shop.website.thm canonical name = shops.myshopify.com

# 2. Querying TXT Security Records to capture the lab flag
user@thm:~$ nslookup --type=TXT website.thm
Server:     127.0.0.0.53
Address:    127.0.0.0.53#53

Non-authoritative answer:
website.thm text = "THM{7012BBA60997F35A9516C2E16D2944FF}"

# 3. Querying MX Mail Exchangers to pinpoint primary routing limits
user@thm:~$ nslookup --type=MX website.thm
Server:     127.0.0.0.53
Address:    127.0.0.0.53#53

Non-authoritative answer:
website.thm mail exchanger = 30 alt4.aspmx.l.google.com
