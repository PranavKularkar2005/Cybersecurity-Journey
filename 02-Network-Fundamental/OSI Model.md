# 🗺️ TryHackMe Room: OSI Model Fundamentals

This repository serves as a structured technical index covering the **Open Systems Interconnection (OSI) Model**. Mastering this reference framework is highly critical for a Security Analyst to establish a systematic mental model for troubleshooting network infrastructure anomalies, isolating threat vectors, and analyzing packet data flow.

---

## 🏗️ Task 1: What is the OSI Model?

The **OSI Model** is a foundational reference framework used in networking that dictates exactly how all heterogeneous networked devices send, receive, and interpret data over a media layer.

### Core Architecture Mechanisms:
* **Uniform Standardization:** It ensures that devices built with completely different internal architectures or by different manufacturers can communicate transparently.
* **Encapsulation Process:** As data flows from the upper human-facing layer down to the physical wire components, each layer executes specific processes and wraps the data with specific protocol control headers. This mechanism of adding protocol information to the payload is called **Encapsulation**.

---

## 🔌 Task 2: Layer 1 - The Physical Layer

The **Physical Layer** is the lowest structural layer of the OSI architecture stack and represents the tangible hardware components responsible for moving raw data streams.

### Key Characteristics:
* **Data Representation:** Tracks data purely through **Electrical Signals** passing across a **Binary Numbering System** composed of raw 1s and 0s.
* **Hardware Scope:** Encompasses physical infrastructure assets, most notably **Ethernet Cables**, fiber optic lines, electrical pins, and network jacks.

---

## 🏷️ Task 3: Layer 2 - The Data Link Layer

The **Data Link Layer** focuses heavily on handling **Physical Addressing** across a local network media channel to coordinate frame routing.

### Key Characteristics:
* **Hardware Interface:** Every network-enabled asset leaves the factory with a specialized piece of hardware called a **Network Interface Card (NIC)**. 
* **Physical Addresses:** The NIC features a unique, permanent, physical identifier assigned directly by the hardware manufacturer called a **MAC Address** (Media Access Control). While MAC configurations are physically hardcoded into the card layout, they can be spoofed by a threat actor during an attack.
* **Transmission Formatting:** This layer receives data structures passed down from the Network layer above it and reformats them into a structure suitable for transmission over the local Physical wires.

---

## 🛣️ Task 4: Layer 3 - The Network Layer

The **Network Layer** handles logical network addressing and routing across different networks to ensure data packets find their target destination.

### Key Characteristics:
* **Addressing Scheme:** Operates entirely using logical **IP Addresses** to identify hosts across disparate networks globally.
* **Optimal Routing:** This layer determines the most optimal path across network boundaries. Packets explicitly evaluate real-time routes to take the fastest and most stable path available.
* **Core Protocols Utilized:**
    1. **OSPF (Open Shortest Path First):** A link-state routing protocol used to locate the shortest path for packets through a local autonomous network system.
    2. **RIP (Routing Information Protocol):** A distance-vector routing protocol that uses hop count as a primary routing metric to find path choices.

### 🏆 Task 1 to 4 Knowledge Verification:
* What does the "OSI" in "OSI Model" stand for? $\rightarrow$ `Open Systems Interconnection`
* How many layers (in digits) does the OSI model have? $\rightarrow$ `7`
* What is the key term for when pieces of information get added to data? $\rightarrow$ `encapsulation`
* What is the name of Layer 1? $\rightarrow$ `Physical`
* What is the name of the numbering system that is both 0's and 1's? $\rightarrow$ `Binary`
* What is the name of the cables that are used to connect devices? $\rightarrow$ `Ethernet Cables`
* What is the name of Layer 2? $\rightarrow$ `Data Link`
* What is the name of the piece of hardware that all networked devices come with? $\rightarrow$ `Network Interface Card`
* What is the name of Layer 3? $\rightarrow$ `Network`
* Will packets take the most optimal route across a network? (Y/N) $\rightarrow$ `Y`
* What does the acronym "OSPF" stand for? $\rightarrow$ `Open Shortest Path First`
* What does the acronym "RIP" stand for? $\rightarrow$ `Routing Information Protocol`
* What type of addresses are dealt with at this layer? $\rightarrow$ `IP Addresses`

---

## 🚛 Task 5: Layer 4 - The Transport Layer

The **Transport Layer** plays a vital role in transmitting data across a network by determining how data chunks are divided, tracked, and delivered between devices. It relies on two main protocols:

### 1. TCP (Transmission Control Protocol)
* **Design Philosophy:** Engineered with absolute reliability and delivery guarantees in mind.
* **Mechanism:** It reserves a constant connection between two devices for the entire duration of the data transfer window.
* **Error Checking:** TCP incorporates error checking to guarantee that data broken down into small chunks is received and reassembled accurately in the exact correct order.
* **Pros & Cons:** It guarantees accuracy and prevents data flooding by synchronizing devices, but it is significantly slower than UDP because it performs a lot more background verification processes.
* **Common Use Cases:** Web browsing, file sharing, and sending emails (where losing half a file makes the data useless).

### 2. UDP (User Datagram Protocol)
* **Design Philosophy:** Engineered for raw speed and minimal overhead.
* **Mechanism:** It does not reserve a continuous connection or perform advanced error checking. It sends data chunks regardless of whether the receiving computer gets them or not. There is no synchronization or delivery guarantee.
* **Common Use Cases:** Video streaming, online gaming, and lightweight discovery protocols (like ARP and DHCP) where speed is vital and minor data loss (like a pixelated frame) is acceptable.

### 🏆 Task 5 Knowledge Verification:
* What is the name of this Layer? $\rightarrow$ `Transport`
* What does TCP stand for? $\rightarrow$ `Transmission Control Protocol`
* What does UDP stand for? $\rightarrow$ `User Datagram Protocol`
* What protocol guarantees the accuracy of data? $\rightarrow$ `TCP`
* What protocol doesn't care if data is received or not by the other device? $\rightarrow$ `UDP`

---

## 🤝 Task 6: Layer 5 - The Session Layer

The **Session Layer** is responsible for establishing, managing, maintaining, and tearing down communication lines between systems.

### Key Characteristics:
* **Session Creation:** Once data has been correctly formatted by Layer 6, the Session layer establishes an active connection to the destination computer. While this connection remains active, a unique session exists.
* **Checkpoints & Efficiency:** It can insert structural "checkpoints" into the data transfer stream. If a connection drops midway, only the data blocks following the newest checkpoint need to be resent, saving valuable network bandwidth.
* **Isolation:** Sessions are unique; data cannot cross over into a different session—it travels strictly within its designated channel.

### 🏆 Task 6 Knowledge Verification:
* What is the name of this layer? $\rightarrow$ `Session`
* What is the technical term for when a connection is successfully established? $\rightarrow$ `Session`

---

## 🎨 Task 7: Layer 6 - The Presentation Layer

The **Presentation Layer** acts as the universal translator for data moving between the network layer standards and the actual software applications.

### Key Characteristics:
* **Standardization & Translation:** Since software developers write code differently, this layer standardizes the payload formatting so it can be handled uniformly by the receiving host, regardless of how the local software application operates underneath.
* **Security & Cryptography:** Crucial security processes such as **Data Encryption** and decryption (e.g., handling HTTPS secure web sessions) take place directly at this layer.

### 🏆 Task 7 Knowledge Verification:
* What is the name of this Layer? $\rightarrow$ `Presentation`

---

## 📱 Task 8: Layer 7 - The Application Layer

The **Application Layer** provides the interface and rules that determine how user-facing software applications interact with network data protocols.

### Key Characteristics:
* **User Interface Mapping:** Provides a friendly Graphical User Interface (GUI) or application protocol interface for software clients (such as email clients, web browsers, or file browsers like FileZilla).
* **Core Application Protocols:**
    * **DNS (Domain Name System):** Resolves human-readable website addresses (URLs) into machine-readable IP addresses.

---

## 🏆 Task 9: Practical - OSI Game

* **Laboratory Simulation Flag:** `THM{OSI_D_E_S_C_A_P_E_D}`
