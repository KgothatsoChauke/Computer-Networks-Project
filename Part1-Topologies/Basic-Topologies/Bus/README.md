# Bus Topology

## Overview
A bus topology where all devices are connected to a single central cable (the bus).

## Characteristics
- **Layout**: Linear backbone cable
- **Advantages**: Simple, minimal cabling
- **Disadvantages**: Single point of failure, performance degrades with heavy traffic

## Network Configuration
- **Total Devices**: [Number of devices]
- **IP Scheme**: [Your IP range, e.g., 192.168.1.0/24]

## Devices Used
- [Number] PCs
- [Number] Switches/Hubs
- [Other devices]

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway |
|--------|------------|-------------|-----------------|
| PC0    | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1    | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| [Add all your devices] | | | |

## Screenshots
1. [Topology Diagram](./screenshots/topology-view.png)
2. [Device Configuration](./screenshots/device-config.png)
3. [Connectivity Test](./screenshots/ping-test.png)

## Verification
- ✅ All devices can communicate
- ✅ IP addresses properly assigned
- ✅ No connectivity issues
