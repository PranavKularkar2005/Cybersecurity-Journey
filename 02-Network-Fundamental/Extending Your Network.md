# 🌐 TryHackMe Room: Extending Your Network

This repository contains my structured technical notes, edge routing designs, and firewall configuration rules for the **Extending Your Network** room under the Network Fundamentals module. Mastering these edge-defense mechanisms is critical for a Security Analyst to interpret perimeter traffic rules, analyze VPN tunneling paths, and protect internal corporate subnets from public threats.

---

## 🔌 Task 1: Introduction to Port Forwarding

Port forwarding is an essential component in connecting external applications and public services to the Internet. Without port forwarding, applications and services running on local servers are exclusively available to devices residing within the same direct network (**Intranet**).

### Core Network Flow:
* **The Intranet Restriction:** If a local database or web server with a private IP address of `192.168.1.10` runs on port `80`, only other local computers within that direct internal network segment can communicate with it.
* **The Solution:** To make the internal website accessible to the public internet, port forwarding must be configured on the network's perimeter device. This explicitly maps a public-facing port on the edge gateway (e.g., `82.62.51.70:80`) directly down to the private internal hosting resource (`192.168.1.10:80`).

### Operational Distinction: Port Forwarding vs. Firewalls
* **Port Forwarding:** Acts as the routing path that explicitly *opens* specific logical port channels on the edge gateway.
* **Firewalls:** Determine *if* incoming data packets are authorized, clean, or safe enough to travel across those open port lanes.

### 🏆 Task 1 Knowledge Verification
* What is the name of the device that is used to configure port forwarding? $\rightarrow$ `router`

---

## 🧱 Task 2: Firewalls 101

A **firewall** is a dedicated security device within a network infrastructure responsible for determining what traffic is allowed to enter and exit. Think of a firewall as the border security check station for a private network perimeter.

Network administrators configure explicit firewall rule sets to **permit** or **deny** data packets based on a combination of core variables:
* **Source Subnet:** Where the traffic is coming from (accepting/denying specific source IP pools).
* **Destination Subnet:** Where the traffic is attempting to travel to.
* **Port Filtering:** Identifying the target application layer channel (e.g., inspecting port `80` only).
* **Protocol Rules:** Evaluating the specific Layer 4 protocol behavior (UDP, TCP, or both).

Firewalls perform packet inspection to enforce these rules. They range from enterprise dedicated hardware appliances to lightweight host software packages (like **Snort**).

### The Two Primary Firewall Categories:

| Firewall Category | Core Technical Behavioral Profile | Resource Cost |
| :--- | :--- | :--- |
| **Stateful** | Tracks and monitors the entire context of a network connection lifecycle. It dynamically checks if packets belong to an active, legitimate exchange (like a verified TCP handshake). If a host connection exhibits malicious history, the firewall blocks the entire device. | **High** (Dynamic tracking consumes extensive memory and system processing resources) |
| **Stateless** | Inspects individual packets completely in isolation using a rigid, static set of filtering rules. If a single bad packet is detected, it drops that block without necessarily blacklisting the entire sending host. It is less advanced but highly effective at handling massive raw traffic volumes (like mitigating a DDoS attack). | **Low** (Static rules consume minimal system resources) |

---

## 🕹️ Task 3: Practical - Firewall Simulation

This section confirms the practical deployment of standard firewall rule sets to filter malicious packets while maintaining unhindered paths for legitimate web clients.

### Interactive Laboratory Parameters:
* **Target Web Server Destination:** `203.0.110.1`
* **Target Filtering Profile:** Block all unauthorized red packets attempting to utilize port `80` while allowing legitimate green packets through safely.
* **Interactive Laboratory Capture Flag:** `THM{FIREWALLS_RULE}`

---

## 🛡️ Task 4: VPN Basics

A **Virtual Private Network (VPN)** is a technology that allows devices on physically separate networks to communicate securely by creating a dedicated, encrypted path between each other over the Internet, known as a **tunnel**. Devices connected within this tunnel form their own private network layer.

### Key Benefits of VPN Deployments:
* **Geographical Interconnection:** Connects separate physical office locations across the globe, allowing employees to access central corporate infrastructure securely.
* **Privacy & Traffic Protection:** Uses strong encryption layers to protect data payloads from sniffing, interception, or manipulation, which is vital over public or unencrypted networks.
* **Anonymity:** Masks local client information from intermediary ISPs and tracking engines. *Note:* The level of anonymity provided is entirely dependent on whether the VPN provider logs user connection history.

### Core VPN Technologies:
* **PPP (Point-to-Point Protocol):** Used to handle authentication and provide data encryption using a matching private key and public certificate setup. It cannot leave a network by itself (non-routable).
* **PPTP (Point-to-Point Tunneling Protocol):** The encapsulation technology that allows the data from PPP to travel and leave a network. It is very easy to set up but features weak encryption compared to modern alternatives.
* **IPSec (Internet Protocol Security):** Encrypts data using the existing IP framework. It is more complex to configure but boasts exceptionally strong enterprise-grade encryption.

---

## 🎛️ Task 5: LAN Networking Devices

Network complexity requires different hardware devices operating across distinct layers of the OSI model to dictate data flow.

### 1. Routers (Layer 3)
* It is a router's job to connect separate networks and pass data packets between them using a process called **routing**.
* Routing involves dynamically calculating optimal paths across networks based on factors like **path shortness**, **link reliability**, and **medium speed** (e.g., copper vs. fiber optic).
* Routers feature an interactive management interface (console/web) allowing administrators to define edge security policies, port forwarding, and firewall rules.

### 2. Switches (Layer 2 vs. Layer 3)
Switches aggregate local devices using Ethernet cables, but they operate across different logical layers:
* **Layer 2 Switches:** Solely responsible for forwarding data frames locally. They keep track of which MAC address is connected to which physical port, mapping delivery streams precisely to the target device instead of repeating traffic to all ports like a hub. They *cannot* operate or route at Layer 3.
* **Layer 3 Switches:** More sophisticated devices that perform all the frame-forwarding duties of a Layer 2 switch but incorporate basic routing capabilities to pass packets between different IP subnets using the IP protocol.

### 3. VLAN (Virtual Local Area Network)
A technology that allows specific devices within a physical network to be split up virtually into separate logical networks. Devices within a specific VLAN (e.g., Sales vs. Accounting) can access the public Internet but are strictly blocked from communicating with each other, adding robust internal segmentation.

### 🏆 Task 5 Knowledge Verification
* What is the verb for the action that a router does? $\rightarrow$ `routing`
* What are the two different layers of switches? Separate these by a comma $\rightarrow$ `Layer 2,Layer 3`

---

## 💻 Task 6: Practical - Network Simulator Challenge

This section validates the end-to-end traversal of data packets across a simulated corporate environment, tracking the precise network logs generated during a standard TCP handshake session.

* **Simulation Task:** Send a verified TCP packet from `computer1` to `computer3` across intermediate routing hops.
* **How many HANDSHAKE entries are there in the Network Log?** $\rightarrow$ `5`
* **Network Simulator Capture Flag:** `THM{YOU'VE_GOT_DATA}`
