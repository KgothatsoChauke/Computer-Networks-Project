# Star Topology

## Overview
Centralized network topology with all devices connected to a central device.

## Characteristics
- **Layout**: All devices connect to central switch/hub
- **Advantages**: Easy to install and manage, easy to add new devices, fault isolation
- **Disadvantages**: Central device single point of failure, requires more cabling than bus

## Network Configuration
- **Total Devices**: [e.g., 6 PCs, 1 Switch]
- **IP Scheme**: [e.g., 192.168.1.0/24]
- **Central Device**: [Switch/Hub - specify model if known]
- **Cabling**: [e.g., Straight-through UTP cables]

## Devices Used
- [Number] PCs
- [1] [Switch/Hub] as central device
- [Any other devices]

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway | Port |
|--------|------------|-------------|-----------------|------|
| [PC0] | [192.168.1.10] | [255.255.255.0] | [192.168.1.1] | [FastEthernet0/1] |
| [PC1] | [192.168.1.11] | [255.255.255.0] | [192.168.1.1] | [FastEthernet0/2] |
| [Add all devices with switch ports] | | | | |

## Configuration Notes
- Central device: [Switch provides dedicated bandwidth / Hub shares bandwidth]
- VLAN configuration: [None / Specify if used]
- Spanning Tree Protocol: [Enabled/Disabled]

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Star network layout*

![Central Device](./screenshots/device-config.png)
*Switch/hub configuration*

![Connectivity Test](./screenshots/ping-test.png)
*Device communication tests*

## Verification
- ✅ All devices can communicate through central device
- ✅ Central device failure isolates devices (tested)
- ✅ No cross-device interference
- ✅ Easy device addition demonstrated
