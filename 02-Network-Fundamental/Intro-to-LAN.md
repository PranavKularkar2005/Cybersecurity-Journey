# 🌐 TryHackMe Room: Intro to LAN

This repository contains my comprehensive technical notes, core takeaways, and lab verification for the **Intro to LAN** room under the Network Fundamentals module. Understanding these concepts is vital for monitoring internal network traffic and identifying anomalous host behaviors.

---

## 📐 Task 1: Introducing LAN Topologies
A Local Area Network (LAN) topology refers to the design, look, and structural arrangement of devices on a network. 

### Core Topologies Evaluated:
*   **Star Topology:** Devices are individually connected via a central networking device such as a switch or hub. It is highly scalable and the most commonly found topology today due to its reliability, though it features a single point of failure if the central device drops.
*   **Bus Topology:** This network layout relies upon a single connection known as a backbone cable. It is highly cost-efficient and easy to set up, but it suffers from severe data bottlenecks under heavy utilization and completely lacks redundancy if the backbone cable breaks.
*   **Ring Topology:** Also known as a token topology, devices are connected directly to each other to form a loop. Data travels in only one direction across the circle, making troubleshooting straightforward. However, a single cut cable or broken device will cause the entire network to break down.

### Core Network Hardware Explained:
1.  **Switch:** A dedicated hardware device designed to aggregate multiple corporate assets (computers, printers, etc.) using Ethernet. It keeps track of which device is connected to which physical port. When a data packet arrives, the switch routes it directly to its intended target port rather than repeating it to every single port, significantly reducing background network traffic.
2.  **Router:** A hardware device whose primary job is to connect different networks and pass data between them using a process called **Routing**. Routing involves calculating and creating efficient data paths between disparate networks so packets can be successfully delivered.

### 🏆 Task 1 Questions & Lab Verification
*   **What does LAN stand for?** `Local Area Network`
*   **What is the verb given to the job that Routers perform?** `Routing`
*   **What device is used to centrally connect multiple devices on the local network and transmit data to the correct location?** `Switch`
*   **What topology is cost-efficient to set up?** `Bus Topology`
*   **What topology is expensive to set up and maintain?** `Star Topology`
*   **Interactive Lab Target Flag:** `THM{TOPOLOGY_FLAWS}`

---

## 🔢 Task 2: A Primer on Subnetting
Subnetting is the technical term for splitting up a network into smaller, miniature networks within itself. Think of it as deciding who gets what slice and reserving a specific section of a larger network infrastructure.

### Why Subnetting is Crucial for Security:
*   **Department Isolation:** In a corporate enterprise, network administrators use subnetting to categorize and assign specific parts of a network to reflect organizational departments (such as Accounting, Finance, and Human Resources). 
*   **Access Control:** By separating departments into individual subnets, security teams can control traffic flow between them. For example, a typical street café implements subnetting to maintain two distinct networks:
    1. One protected network for employees, cash registers, and internal facilities.
    2. One open network for the general public to use as a hotspot.
*   **Operational Benefits:** Subnetting provides critical corporate advantages, including enhanced **Efficiency**, robust **Security**, and **Full control** over network broadcast domains.

### Understanding IP Addressing & Subnet Components:
*   **Structure:** Just like a standard IP address, a subnet mask is represented as a number of four bytes (**32 bits** total), divided into four sections called **octets**. 
*   **Value Range:** Each individual octet section ranges from a minimum of **0 to 255**.

### The 3 Ways Subnets Use IP Addresses:
| Address Type | Core Purpose | Example (Class C) |
| :--- | :--- | :--- |
| **Network Address** | Identifies the start of the actual network and is used to establish a network's existence. | `192.168.1.0` |
| **Host Address** | Used to uniquely identify a specific physical device or endpoint operating on the subnet. | `192.168.1.100` |
| **Default Gateway** | A special address assigned to a device on the network capable of forwarding data packets out to an entirely separate network (such as routing traffic to the Internet). It usually occupies either the first (`.1`) or last (`.254`) host address. | `192.168.1.254` |

### 🏆 Task 2 Questions & Knowledge Verification
*   **What is the technical term for dividing a network up into smaller pieces?** `Subnetting`
*   **How many bits are in a subnet mask?** `32`
*   **What is the range of a section (octet) of a subnet mask?** `0-255`
*   **What address is used to identify the start of a network?** `Network Address`
*   **What address is used to identify devices within a network?** `Host Address`
*   **What is the name used to identify the device responsible for sending data to another network?** `Default Gateway`

---

## 🕵️ Task 3: ARP (Address Resolution Protocol)
Every endpoint on a network relies on two unique identifiers: a physical identifier (**MAC Address**) and a logical identifier (**IP Address**). The Address Resolution Protocol (ARP) is the core technology responsible for allowing devices to map and identify themselves across a Local Area Network.

### How ARP Works:
*   **The Ledger:** Each device on a network maintains a local log or ledger known as an **ARP Cache** to store the identity mappings of other neighboring devices.
*   **ARP Request:** When a device wants to communicate but lacks the target's physical identity, it sends a **broadcast message** to the entire network asking: *"What is the MAC address that owns this IP address?"*
*   **ARP Reply:** The specific device that owns the requested IP address responds directly back with an **ARP Reply** containing its physical MAC address. The initiating device saves this mapping into its cache for future operational use.

### Real-World ARP Traffic Trace (From Lab):
1.  **Broadcast Packet (Request):** `SRC MAC: 01:00:AB:78:99:33` sends to `DST MAC: FF:FF:FF:FF:FF:FF` (Broadcast Address) querying *"Who has IP Address 192.168.1.10"*.
2.  **Unicast Packet (Reply):** The target device responds back directly: `SRC MAC: 18:AC:33:12:88:29` to `DST MAC: 01:00:AB:78:99:33` stating *"I Have IP Address 192.168.1.10"*.

### 🏆 Task 3 Knowledge Verification
*   **What does ARP stand for?** `Address Resolution Protocol`
*   **What category of ARP Packet asks a device whether or not it has a specific IP address?** `Request`
*   **What address is used as a physical identifier for a device on a network?** `MAC Address`
*   **What address is used as a logical identifier for a device on a network?** `IP Address`

---

## 🔌 Task 4: DHCP (Dynamic Host Configuration Protocol)
IP addresses can be assigned manually by an administrator or automatically using a dedicated **DHCP Server**. DHCP eliminates manual errors by dynamically leasing out configurations to endpoints joining a network.

### The 4-Step DHCP Process (D.O.R.A.):
1.  **DHCP Discover:** When an unconfigured endpoint boots onto the network, it broadcasts a request to see if any DHCP servers are active: *"Hey, I'm new here, is there anyone who can give me an IP Address?"*
2.  **DHCP Offer:** An active DHCP server replies with a usable configuration offer: *"Hey! Sure thing, you can have 192.168.1.10."*
3.  **DHCP Request:** The client machine sends a reply back confirming it wishes to lease that specific address: *"Yes, that would be brilliant! I'll start using 192.168.1.10."*
4.  **DHCP ACK (Acknowledgment):** The server sends a final acknowledgment packet confirming the transaction is complete: *"Okay, great. You can use that IP Address for the next 24 hours."*

### 🏆 Task 4 Knowledge Verification
*   **What type of DHCP packet is used by a device to retrieve an IP address?** `DHCP Discover`
*   **What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?** `DHCP Request`
*   **Finally, what is the last DHCP packet that is sent to a device from a DHCP server?** `DHCP ACK`
