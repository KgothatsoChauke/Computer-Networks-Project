# Bus Topology

## Overview
A bus network topology where all devices are connected to a single backbone cable.

## Characteristics
- **Layout**: Linear bus with drop lines to each device
- **Advantages**: Simple setup, minimal cabling, cost-effective for small networks
- **Disadvantages**: Single point of failure, difficult to troubleshoot, performance degrades with heavy traffic

## Network Configuration
- **Total Devices**: [e.g., 4 PCs, 1 Hub]
- **IP Scheme**: [e.g., 192.168.1.0/24]
- **Backbone Cable**: [e.g., Coaxial cable]
- **Terminators**: [e.g., 2 terminators installed]

## Devices Used
- [Number] PCs
- [Number] Hubs/Switches
- [Number] Terminators

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway |
|--------|------------|-------------|-----------------|
| [PC0] | [192.168.1.10] | [255.255.255.0] | [192.168.1.1] |
| [PC1] | [192.168.1.11] | [255.255.255.0] | [192.168.1.1] |
| [Add all your devices] | | | |

## Configuration Notes
- All devices share the same collision domain
- CSMA/CD protocol used for media access
- Cable length: [specify if relevant]

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Complete bus network layout*

![Device Configuration](./screenshots/device-config.png)
*IP configuration example*

![Connectivity Test](./screenshots/ping-test.png)
*Successful communication test*

## Verification
- ✅ All devices can communicate with each other
- ✅ No IP address conflicts
- ✅ End-to-end connectivity verified
- ✅ Proper termination confirmed
