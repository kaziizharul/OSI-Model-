#  How Data Travels Through the OSI Model
### An Interactive Network Visualization | Educational & Portfolio Project

![Status](https://img.shields.io/badge/status-active-brightgreen) ![Type](https://img.shields.io/badge/type-Interactive%20Visualization-blue) ![Stack](https://img.shields.io/badge/stack-HTML%20%7C%20CSS%20%7C%20JavaScript-orange)

**Author:** Kazi Izharul Islam — B.Sc. in CSE | CCNA

---

##  Overview

This project is an **interactive, animated visualization of the OSI (Open Systems Interconnection) Model**, built to demonstrate — visually and technically — how a single network request travels from a user's device to a web server and back, layer by layer.

Rather than a static diagram, this is a **working simulation**: it animates the actual journey of a data packet across physical infrastructure (device → router → ISP → internet → server) while simultaneously visualizing the **encapsulation and decapsulation** process that happens at each of the seven OSI layers.

It was built as both a **networking/cybersecurity educational tool** and a **portfolio demonstration piece** for LinkedIn and GitHub.

**Live Demo:** [View the interactive artifact](https://github.com/user-attachments/files/32709521/osi-cinematic-video.html)

---

##  Purpose

- Help students, junior engineers, and networking/security learners **visualize an abstract concept concretely**
- Demonstrate the **encapsulation/decapsulation** process that underlies every network request (a core concept in networking, packet analysis, and security tooling like Wireshark)
- Serve as a **CCNA-aligned reference** connecting theory (7 layers) to practice (real headers, ports, protocols)
- Function as a reusable teaching asset for SOC analysts and security students who need to reason about *where* in the stack a threat, log, or control operates

---

##  Features

| Feature | Description |
|---|---|
| **Animated Network Journey** | A glowing packet visibly travels Smartphone → Wi-Fi Router → ISP → Internet → Web Server, then the response returns |
| **7 Interactive OSI Layers** | Click or step through each layer (7→1) to reveal responsibility, protocols, data unit, and a real-world example |
| **Live Encapsulation View** | Watch headers (Ethernet, IP, TCP) wrap around the data in real time as it descends the stack, then unwrap at the server |
| **Playback Controls** | Play, Pause, Reset, Next Layer, Previous Layer |
| **Progress Indicator** | Visual tracker showing current layer position (L7 → L1) |
| **LinkedIn Presentation Mode** | One-click simplified view optimized for screen recording / social sharing |
| **Responsive Design** | Works across desktop and mobile viewports |
| **Technically Accurate Terminology** | Distinguishes IP vs MAC vs Port vs Frame/Packet/Segment/Bit correctly per layer |

---

##  The OSI Model — What It Is and Why It Matters

The **OSI (Open Systems Interconnection) Model** is a 7-layer conceptual framework (ISO standard) that describes how data moves from an application on one device, through a network, to an application on another device. Each layer has a distinct responsibility, and each layer on the sender's side only "talks" to its corresponding layer on the receiver's side (a principle known as **peer-to-peer communication** within the model).

> **Important distinction:** The OSI model is a *teaching and troubleshooting reference*, not literally how the modern Internet is implemented in software. Real-world protocols are more commonly described using the simpler **4-layer TCP/IP model**. However, OSI remains the standard vocabulary for networking, security, and certification exams (CCNA, Security+, etc.) because it isolates *where* a problem or control exists.

### The 7 Layers (Top → Bottom)

| # | Layer | Responsibility | Protocols / Examples | Data Unit |
|---|---|---|---|---|
| 7 | **Application** | Provides network services directly to the end-user application | HTTP, HTTPS, DNS, SMTP | Data |
| 6 | **Presentation** | Formats, encodes, compresses, and encrypts/decrypts data | TLS/SSL concepts, JPEG, JSON, UTF-8 | Data |
| 5 | **Session** | Establishes, manages, and terminates communication sessions | Session/logical connection management | Data |
| 4 | **Transport** | End-to-end delivery, segmentation, reliability, port addressing | TCP (reliable), UDP (fast, connectionless) | Segment / Datagram |
| 3 | **Network** | Logical addressing and routing between different networks | IPv4, IPv6 | Packet |
| 2 | **Data Link** | Local network delivery and physical addressing (framing) | Ethernet, Wi-Fi (802.11) | Frame |
| 1 | **Physical** | Transmits raw bits as electrical, optical, or radio signals | Ethernet cable, fiber optic, Wi-Fi radio | Bits |

---

##  How It Works — Full Request Example

**Scenario:** You open a browser on your smartphone and visit `https://example.com`.

### Step 1 — Sender side: Encapsulation (Layer 7 → Layer 1)

1. **Layer 7 (Application):** Your browser generates an `HTTP(S)` request — "GET the homepage of example.com."
2. **Layer 6 (Presentation):** The request is encrypted (TLS, since it's HTTPS) and formatted (e.g., text encoded in UTF-8).
3. **Layer 5 (Session):** A logical session is established and tracked between your browser and the server so the conversation stays coherent.
4. **Layer 4 (Transport):** The data is broken into a **TCP segment**. A **destination port (443 for HTTPS)** is attached, along with sequencing info for reliable delivery.
5. **Layer 3 (Network):** The segment is wrapped into an **IP packet**. Your device's private IP (e.g., `192.168.0.10`) is set as the source, and the web server's public IP as the destination.
6. **Layer 2 (Data Link):** The packet is wrapped into an **Ethernet/Wi-Fi frame**, tagged with your device's **source MAC address** and your router's **destination MAC address** (MAC only matters for this local hop, not the entire journey).
7. **Layer 1 (Physical):** The frame is converted into raw **bits** (radio signals over Wi-Fi) and transmitted.

### Step 2 — Traversal

The bits travel: **Smartphone → Wi-Fi Router → ISP → Internet backbone routers → Web Server.**
At every router hop, Layer 2 (MAC) information is *replaced* for the next local hop, while the Layer 3 (IP) source/destination stays consistent end-to-end — this is the key distinction between MAC and IP addressing.

### Step 3 — Receiver side: Decapsulation (Layer 1 → Layer 7)

The web server receives the bits and reverses the process — unwrapping the frame, then the packet, then the segment — until the original HTTP(S) request is reconstructed at Layer 7, where the server processes it and prepares a response.

### Step 4 — The Response

The exact same encapsulation → transmission → decapsulation cycle happens in reverse: the server's response is wrapped from Layer 7 down to Layer 1, transmitted back across the internet, and unwrapped by your smartphone until the webpage renders in your browser.

---

## Why This Matters for Security (SOC / Threat Detection Context)

Understanding which OSI layer a technology or attack operates at is foundational for SOC and network security work:

- **Layer 2 attacks:** ARP spoofing, MAC flooding
- **Layer 3 attacks:** IP spoofing, routing attacks
- **Layer 4 attacks:** SYN floods, port scanning
- **Layer 7 attacks:** SQL injection, XSS, HTTP-based DDoS

Firewalls, IDS/IPS, and SIEM rules are frequently described by *which layer they inspect* — a packet-filtering firewall works at Layers 3/4, while a Web Application Firewall (WAF) operates at Layer 7. This mental model directly supports log analysis, alert triage, and control placement in a SOC environment.

---

##  Tech Stack

- **HTML5 / CSS3** — layout, responsive grid, dark cybersecurity-themed UI
- **Vanilla JavaScript** — animation logic, state management, interactivity (no external frameworks/dependencies)
- Fully self-contained single-file build — no build step required

---

## Usage

1. Clone or download this repository
2. Open `osi-model.html` in any modern browser — or view the [live hosted version](https://github.com/user-attachments/files/32709521/osi-cinematic-video.html)
3. Click **▶ Play** to watch the automatic packet journey, or manually click through Layers 7→1 to explore each one
4. Toggle **LinkedIn Presentation Mode** for a simplified view suited to screen recording

---

##  Notes on Technical Accuracy

- OSI is presented as a **conceptual reference model**, not a literal implementation of the modern Internet
- IP (logical/routing) and MAC (local delivery) addressing are explicitly distinguished
- Port numbers are correctly scoped to Layer 4 (transport-layer service identification)
- Data unit terminology is used precisely per layer: **Bits (L1) → Frame (L2) → Packet (L3) → Segment/Datagram (L4) → Data (L5–L7)**

---

## License

Shared for educational and portfolio purposes. Feel free to fork, adapt, and use for your own learning or teaching materials with attribution.

---

##  Author

**Kazi Izharul Islam**
B.Sc. in Computer Science & Engineering | CCNA
Focus: Cybersecurity, SOC Automation, AI Agent Development, Network Security
