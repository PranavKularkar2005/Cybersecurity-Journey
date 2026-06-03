# 📦 TryHackMe Room: Packets & Frames

This repository contains my structured technical notes, protocol header breakdowns, and architectural flow diagrams for the **Packets & Frames** room under the Network Fundamentals module. Understanding these packet structures is mandatory for analyzing network logs and pinpointing protocol-specific exploits.

---

## ✉️ Task 1: What are Packets and Frames

Packets and frames are small slices of a larger message data stream that travel across network paths. Standardizing and fragmenting transmissions into smaller pieces prevents large messages from causing network bottlenecks.



### The Core Difference:
* **Packet:** A piece of data originating at **Layer 3 (Network Layer)** of the OSI model. It primarily encapsulates your data payload alongside logical IP addressing information. If it features an IP address, it is a packet.
* **Frame:** A piece of data operating at **Layer 2 (Data Link Layer)**. A frame encapsulates the Layer 3 packet by wrapping it with physical hardware addressing parameters, such as source and destination **MAC Addresses**. When logical routing configurations are stripped away, you are dealing with a frame.

### The Postal Analogy:
Think of mailing a physical letter. The written document inside is the **packet**, while the outer protective envelope is the **frame**. The envelope contains the physical routing data needed to move the contents across local delivery stops. Once a receiver opens the envelope (frame), they can read the inner document (packet) to figure out how to process the actual contents.

### Essential Internet Protocol (IP) Headers:
| IP Header Field | Core Technical Description |
| :--- | :--- |
| **Time to Live (TTL)** | Sets a specific expiry timer on a packet. This prevents dropped or unroutable packets from bouncing indefinitely and clogging network resources. |
| **Checksum** | Provides robust integrity verification for protocols across the TCP/IP stack. If data bits are altered or corrupted in transit, the calculated checksum value will mismatch, marking the packet corrupt. |
| **Source Address** | The logical IP address of the explicit host sending the data, ensuring the receiver knows where to send return responses. |
| **Destination Address** | The target IP address of the device intended to receive the packet, defining its overall routing path. |

### 🏆 Task 1 Knowledge Verification
* What is the name for a piece of data when it **does have** IP addressing information? $\rightarrow$ `Packet`
* What is the name for a piece of data when it **does not have** IP addressing information? $\rightarrow$ `Frame`

---

## 🤝 Task 2: TCP/IP & The Three-Way Handshake

The **Transmission Control Protocol (TCP)** is a connection-based network standard that guarantees data integrity and reliable packet sequencing. 

Unlike stateless protocols, TCP requires an explicit connection to be successfully established between a client and a target server **before** any application data layer bytes can be transmitted.

### The TCP Model Layering Layout:
The TCP/IP stack can be viewed as a streamlined, highly summarized version of the 7-layer OSI model, compressed into **4 layers**:
1. Application
2. Transport
3. Internet
4. Network Interface

### Vital TCP Header Structural Fields:
* **Source Port:** A port opened randomly by the sending machine (from an available pool of unassigned ports between `0-65535`) to send the segment out.
* **Destination Port:** The explicit port number that a target service or daemon is listening on at the remote system (e.g., HTTP Web servers default to port `80`). This is never chosen at random.
* **Source IP / Destination IP:** The logical network locator strings marking the specific sender interface and the target destination system.
* **Sequence Number:** A random Initial Sequence Number (ISN) assigned to the first data block to track chunks and ensure accurate host reassembly.
* **Acknowledgment Number:** Tracks data receipt tracking by taking the current sequence number and incrementing it by 1 (`Sequence Number + 1`).
* **Checksum:** A mathematical calculation output value that grants complete data block integrity verification. If the calculation output changes at the destination, the payload is corrupt.
* **Data:** The actual payload storage block holding the raw bytes of the file being transmitted.
* **Flag:** Special single-bit parameters embedded inside the header tracking how a segment must be parsed by endpoints during the session lifecycle.

### The Three-Way Handshake Flow Mechanics (Session Establishment):



```text
Client (Alice)                                    Server (Bob)
     |                                                 |
     | ------------ [1. SYN (ISN = 0)] --------------> |
     |                                                 |
     | <------- [2. SYN/ACK (ISN=5000, ACK=1)] -------- |
     |                                                 |
     | ------------- [3. ACK (ISN=1)] ---------------> |
     v                                                 v
[CONNECTED]                                      [CONNECTED]
