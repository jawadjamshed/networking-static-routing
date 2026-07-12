# Networking - Static Routing

A Cisco Packet Tracer project demonstrating the implementation of **Static Routing** using Cisco IOS. This lab focuses on manually configuring routes between multiple routers to enable communication across different networks.

## 📌 Project Overview

Static Routing is one of the fundamental routing techniques used in computer networks. In this project, multiple routers are interconnected through serial links, and static routes are manually configured to establish end-to-end connectivity between different LANs.

This project is designed for students learning CCNA, computer networking, and Cisco router configuration.

## 🎯 Objectives

- Configure IPv4 addressing on routers and end devices
- Configure static routes on Cisco routers
- Verify routing tables
- Test end-to-end connectivity using Ping and Traceroute
- Understand how manually configured routes work

## 🖥️ Network Topology

![Network Topology](topology.png)

*(Brief description: e.g. R1–R2–R3 connected via serial links, each router has a LAN with PCs)*

## 🌐 IP Addressing Table

| Device | Interface | IP Address | Subnet Mask |
|--------|-----------|------------|--------------|
| R1     | Gig0/0    |            |              |
| R1     | Serial0/0/0 |          |              |
| R2     | ...       |            |              |

## 📂 Repository Structure

\```text
networking-static-routing/
│
├── README.md
├── topology.png
├── static-routing.pkt
│
└── configs/
    ├── R1.txt
    ├── R2.txt
    └── R3.txt
\```

## 🛠️ Technologies Used

- Cisco Packet Tracer
- Cisco IOS
- IPv4 Addressing
- Static Routing
- Serial Communication

## 🚀 How to Use

1. Clone or download this repository
2. Open `static-routing.pkt` using Cisco Packet Tracer
3. Review each router configuration inside the `configs` folder
4. Verify routing using Cisco IOS commands

## ✅ Verification Commands

\```bash
show ip route
show running-config
show ip interface brief
ping
traceroute
\```

## 📖 Learning Outcomes

After completing this lab, you should be able to:

- Configure static routes
- Understand routing table entries
- Verify router connectivity
- Troubleshoot routing issues
- Understand manual path selection

## 📄 License

This project is shared for educational purposes.

## 👨‍💻 Author

Alpha
