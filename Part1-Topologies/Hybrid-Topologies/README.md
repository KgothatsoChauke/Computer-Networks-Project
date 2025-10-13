# 🏢 Hybrid Network Topology Project

## 📋 Project Overview
This project implements an enterprise-grade **hybrid network** integrating four distinct network topologies alongside advanced features such as IPv4/IPv6 dual-stack, VLAN segmentation, ACL-based security, and enterprise services.  
It demonstrates real-world **enterprise network design principles** suitable for medium to large organizations.

---

# 🌐 Network Architecture

### Core Design
```
        [ R-Core ] (10.0.10.1)
           |
    [ Core-Switch ]
       /    |    \
      /     |     \
 [DistA]  [DistB]  [DistC]
    |       |       /    \
 [Star]   [Ring]  [Mesh] [Bus]
```

---

# Extended Star Topology

## Overview
Hierarchical star topology connecting a distribution router (DistA) to multiple office devices for administrative operations.

## Characteristics
- **Layout**: Centralized star network from DistA
- **Purpose**: Administrative and office operations
- **Advantages**: Easy troubleshooting, centralized management
- **Disadvantages**: Single point of failure at the central switch

## Network Configuration
- **Network**: 10.0.1.0/24  
- **Devices**: Office-PC1, Office-PC2, Office-PC3, File-Server  
- **VLAN**: VLAN 20 (Internal)  
- **Gateway**: 10.0.1.1 (DistA)  

---

# Ring Topology

## Overview
Ring topology connecting DistB to a small branch office network to provide redundancy.

## Characteristics
- **Layout**: Ring with DistB as the central node  
- **Purpose**: Branch office with fault-tolerant connectivity  
- **Advantages**: Fault tolerance, automatic path recovery  
- **Disadvantages**: Troubleshooting can be complex if multiple failures occur

## Network Configuration
- **Network**: 10.0.30.0/24  
- **Devices**: Ring-PC-1, Ring-PC-2, Ring-PC-3  
- **VLAN**: VLAN 30 (Guest/Branch)  
- **Gateway**: 10.0.30.1 (DistB)  

---

# Mesh Topology

## Overview
Fully connected guest network connecting DistC to multiple end devices, maximizing redundancy and alternative paths.

## Characteristics
- **Layout**: Mesh topology for guest access  
- **Purpose**: Guest network access  
- **Advantages**: Maximum redundancy, multiple paths for fault tolerance  
- **Disadvantages**: Higher cabling and configuration complexity  

## Network Configuration
- **Network**: 10.0.50.0/24  
- **Devices**: Guest-PC-1, Guest-PC-2, Guest-PC-3, Guest-PC-4  
- **Gateway**: 10.0.50.1 (DistC)  

---

# Bus Topology

## Overview
Bus network connecting DistC to peripheral devices like printers and IoT devices.

## Characteristics
- **Layout**: Single shared medium bus connecting multiple devices  
- **Purpose**: Peripheral and IoT device network  
- **Advantages**: Simple to expand, minimal infrastructure required  
- **Disadvantages**: Single cable failure affects the entire network segment  

## Network Configuration
- **Network**: 10.0.40.0/24  
- **Devices**: Network-Printer-1, Network-Printer-2, Network-Printer-3  
- **Gateway**: 10.0.40.1 (DistC)  

---

# ⚡ Technical Features

## Network Protocols & Services
- ✅ IPv4 Static Routing  
- ✅ IPv6 Dual-Stack  
- ✅ VLAN Segmentation (3 VLANs)  
- ✅ DNS Services  
- ✅ HTTP Web Server  
- ✅ Spanning Tree Protocol (STP)  

## Security Implementation
- ✅ Access Control Lists (ACLs)  
- ✅ SSH Remote Management  
- ✅ Port Security  
- ✅ Guest Network Restrictions  
- ✅ Inter-VLAN Routing  

---

# 🛠️ IP Addressing Scheme

## IPv4 Addressing Table
| Device | Interface | IP Address | Subnet Mask | Gateway | Purpose |
|--------|-----------|------------|------------|---------|---------|
| R-Core | Gig0/0.10 | 10.0.10.1 | 255.255.255.0 | N/A | VLAN 10 Gateway |
| R-Core | Gig0/0.20 | 10.0.20.1 | 255.255.255.0 | N/A | VLAN 20 Gateway |
| R-Core | Gig0/0.30 | 10.0.40.1 | 255.255.255.0 | N/A | VLAN 30 Gateway |
| DistA | Gig0/0 | 10.0.10.4 | 255.255.255.0 | 10.0.10.1 | Core Link |
| DistA | Gig0/1.30 | 10.0.200.1 | 255.255.255.0 | N/A | Office Network |
| DistB | Gig0/0 | 10.0.10.2 | 255.255.255.0 | 10.0.10.1 | Core Link |
| DistB | Gig0/1 | 10.0.30.1 | 255.255.255.0 | N/A | Ring Network |
| DistC | Gig0/0 | 10.0.10.3 | 255.255.255.0 | 10.0.10.1 | Core Link |
| DistC | Gig0/1 | 10.0.50.1 | 255.255.255.0 | N/A | Guest Network |
| DistC | Gig0/2 | 10.0.40.1 | 255.255.255.0 | N/A | Printer Network |

## End Device IP Addressing
| Device | IP Address | Subnet Mask | Gateway | DNS |
|--------|------------|------------|--------|-----|
| Web-Server | 10.0.10.10 | 255.255.255.0 | 10.0.10.1 | 10.0.10.10 |
| Office-PC1 | 10.0.1.10 | 255.255.255.0 | 10.0.1.1 | 10.0.10.10 |
| File-Server | 10.0.1.20 | 255.255.255.0 | 10.0.1.1 | 10.0.10.10 |
| Ring-PC-1 | 10.0.30.10 | 255.255.255.0 | 10.0.30.1 | 10.0.10.10 |
| Guest-PC-1 | 10.0.50.10 | 255.255.255.0 | 10.0.50.1 | 10.0.10.10 |
| Printer-1 | 10.0.40.10 | 255.255.255.0 | 10.0.40.1 | N/A |

## IPv6 Addressing Scheme
| Network Segment | IPv6 Prefix | Gateway |
|-----------------|------------|---------|
| Core Network | 2001:DB8:ACAD:10::/64 | 2001:DB8:ACAD:10::1 |
| Office Network | 2001:DB8:ACAD:1::/64 | 2001:DB8:ACAD:1::1 |
| Ring Network | 2001:DB8:ACAD:30::/64 | 2001:DB8:ACAD:30::1 |
| Guest Network | 2001:DB8:ACAD:50::/64 | 2001:DB8:ACAD:50::1 |
| Printer Network | 2001:DB8:ACAD:40::/64 | 2001:DB8:ACAD:40::1 |

---

# 🔧 Configuration Notes

## VLAN Configuration
```bash
vlan 10
 name SERVERS
vlan 20
 name INTERNAL
vlan 30
 name GUEST

interface FastEthernet0/2
 switchport mode access
 switchport access vlan 10

interface GigabitEthernet0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
```

## Router-on-a-Stick
```bash
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 10.0.10.1 255.255.255.0
 ipv6 address 2001:DB8:ACAD:10::1/64

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 10.0.20.1 255.255.255.0
 ipv6 address 2001:DB8:ACAD:20::1/64

interface GigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 10.0.40.1 255.255.255.0
 ipv6 address 2001:DB8:ACAD:40::1/64
```

## Security Configurations
```bash
username admin privilege 15 secret admin123
line vty 0 4
 transport input ssh
 login local

interface range FastEthernet0/2-4
 switchport mode access
 switchport port-security
 switchport port-security maximum 2
 switchport port-security violation restrict
```

## DNS Service Records
```
webserver.local    → 10.0.10.10
fileserver.local   → 10.0.1.20
officepc1.local    → 10.0.1.10
ringpc1.local      → 10.0.30.10
guestpc1.local     → 10.0.50.10
printer1.local     → 10.0.40.10
```

---

# 📊 Testing & Verification

## Connectivity Tests
- ✅ Cross-topology communication verified  
- ✅ Inter-VLAN routing verified  
- ✅ DNS resolution across networks  
- ✅ IPv6 dual-stack functionality confirmed  
- ✅ Redundancy testing for Ring & Mesh topologies  

## Security Verification
- ✅ Guest network restrictions functional  
- ✅ SSH remote management operational  
- ✅ Port security preventing unauthorized devices  
- ✅ ACL traffic filtering enforced  

---

# 🎯 Project Achievements
- ✅ Hybrid design integrating four topologies  
- ✅ Enterprise-level security implementation  
- ✅ Dual-stack IPv4 & IPv6 operation  
- ✅ Centralized DNS and web services  
- ✅ Redundant and fault-tolerant network paths  
- ✅ Complete IP addressing, configuration, and testing documentation  

---

# 📁 Project Structure
```
Hybrid-Network-Project/
├── README.md
├── IP-Addressing-Tables.md
├── Configuration-Guide.md
├── Network-Topology-Diagrams.md
├── Security-Implementation.md
├── Testing-Results.md
└── Screenshots/
    ├── topology-overview.png
    ├── connectivity-tests/
    ├── security-features/
    ├── vlan-configuration/
    └── service-verification/
```

---

# 🚀 Getting Started

## Prerequisites
- Cisco Packet Tracer 8.x or higher  
- Basic understanding of networking concepts  
- Access to network simulation environment  

## Instructions
1. Open project file in Packet Tracer  
2. Verify all physical connections (green links)  
3. Test connectivity between different topology segments  
4. Validate VLAN and guest network restrictions  
5. Confirm DNS resolution and web services  
6. Test IPv6 connectivity across all networks  

---

# 👨‍💻 Author
**Kgothatso Chauke**  
Comprehensive hybrid network design, implementation, and documentation.
