# Overview

EchoVoid is a Proof-of-Concept (PoC) tool designed to demonstrate ICMP Tunneling techniques. It bypasses standard firewall rules and traffic inspection by encapsulating arbitrary data within the payload section of ICMP Echo Request (Type 8) packets.
While network administrators focus on TCP/UDP ports, EchoVoid operates in the "background noise" of the network, turning diagnostic tools into a covert communication channel.

# The Mechanism

Standard ICMP packets contain an optional data section usually filled with padding or timestamps.

Encapsulation: EchoVoid intercepts the user's message.
Injection: The message is injected into the payload of a standard Ping packet.
Transmission: The packet traverses the network as a legitimate diagnostic request.
Extraction: The listener captures the packet, discards the header, and reconstructs the hidden message.

# Features

Stealth Communication: No open TCP/UDP ports required on the client side.
Scapy-Based: Utilizes Python's scapy library for raw packet manipulation.
Lightweight: Minimal dependencies, designed for Linux environments (Fedora/Debian compatible).
Custom Payload: Support for string-based message transfer (expandable to file transfer).

# Installation

Clone the repository:
Bash
git clone [https://github.com/egetones/EchoVoid.git](https://github.com/egetones/EchoVoid.git)
cd EchoVoid
Install dependencies (Root privileges required for raw socket access):

Bash
pip install scapy

# Usage
Note: Both scripts require sudo privileges to craft and sniff raw ICMP packets.

1. The Listener (Server)
Start the listener on the destination machine to sniff for incoming covert packets.

Bash
sudo python3 listener.py
2. The Agent (Client)
Send a covert message hidden inside a ping.

Bash
sudo python3 agent.py --target <TARGET_IP> --message "Secret_Payload_Here"
# Disclaimer
EDUCATIONAL PURPOSE ONLY

This project is created for research and educational purposes to demonstrate protocol vulnerabilities. The author takes no responsibility for any misuse of this tool. Use only on networks you own or have explicit permission to test.

Crafted with <3 by Ege
