# OSI Model Project — Interactive Visualizer + Cinematic Explainer

A two-part project exploring the OSI Model: an interactive web visualization you can click through, and a shot-by-shot script for a 40-second cinematic explainer video.

🔗 **Live Portfolio:** [Add your GitHub Pages link here]
🔗 **Interactive Demo:** [Add your visualizer link here]

## Overview

This project breaks down one of networking's most fundamental concepts — how a single request travels through all 7 OSI layers — using two different mediums: a hands-on interactive tool, and a narrative video script designed for a general audience.

## Part 1 — Interactive OSI Model Visualizer

A self-contained HTML/CSS/JS web app demonstrating:
- Animated packet journey: Smartphone → Wi-Fi Router → ISP → Internet → Web Server → back
- 7 clickable OSI layers, each with responsibility, protocols, data unit, and a real-world example
- Live encapsulation/decapsulation view showing headers being added and stripped
- Playback controls (Play, Pause, Reset, Next/Previous Layer)

**Tech:** HTML5, CSS3, vanilla JavaScript — no dependencies, runs in any browser.

## Part 2 — "What Really Happens When You Open a Website?"

A 40-second cinematic 3D/VFX explainer script (storyboard format), written shot-by-shot for production in Blender/Cinema 4D/After Effects or AI video tools (Runway, Pika, Luma, Sora).

**Status:** Script complete — production in progress.

Covers the same journey as Part 1, but as a visual narrative:
1. **00:00–00:04** — The Question (a keystroke births the "hero packet")
2. **00:04–00:08** — Application Layer (HTTPS request created)
3. **00:08–00:13** — Encapsulation (TCP → IP → Ethernet shells lock on)
4. **00:13–00:18** — Physical Transmission (Wi-Fi, Ethernet, fiber — three distinct signal types)
5. **00:18–00:24** — Routing the Internet (IP addressing across network hops)
6. **00:24–00:28** — TCP Handshake (SYN → SYN-ACK → ACK)
7. **00:28–00:32** — Decapsulation (reverse of step 3, at the destination server)
8. **00:32–00:36** — The Response (return trip, visually distinct color trail)
9. **00:36–00:40** — Final Reveal (full journey shown as one arc)

## OSI Layer Reference

| Layer | Name | What's Shown | Data Unit |
|---|---|---|---|
| 7 | Application | Browser / HTTP / HTTPS | Data |
| 6 | Presentation | Encryption concept, compression, formatting | Data |
| 5 | Session | Session setup/teardown | Data |
| 4 | Transport | TCP/UDP, ports, segmentation | Segment/Datagram |
| 3 | Network | IP addressing and routing | Packet |
| 2 | Data Link | MAC addresses, Ethernet/Wi-Fi frames | Frame |
| 1 | Physical | Bits as electrical, radio, or optical signals | Bits |

**Technical accuracy notes:**
- MAC addresses are local-network only and change at every hop — unlike IP addresses, which persist logically across the full journey.
- Port 443/TCP is used as the canonical HTTPS example (HTTP/3 over QUIC/UDP is a known exception, noted but not depicted, to keep the script focused).
- OSI is a conceptual reference model; modern Internet protocols are more commonly described using the TCP/IP model.

## How to Run the Visualizer Locally

```bash
git clone https://github.com/your-username/osi-model-project.git
cd osi-model-project
```

Open `index.html` in any browser — no server or build step required.

## Motivation

Built to strengthen core networking fundamentals — encapsulation, addressing, and transport-layer behavior — while working on cybersecurity, SOC automation, and network security projects.

## Author

**Kazi Izharul Islam**
B.Sc. in Computer Science & Engineering | CCNA
Cybersecurity · Networking · Continuous Learning
[LinkedIn](#) · [GitHub](#)

## License

Open for educational use. Feel free to fork, learn from, and adapt it.
