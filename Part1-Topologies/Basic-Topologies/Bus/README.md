# Bus Topology

## Overview
A bus topology where all devices share a single communication backbone.

## Characteristics
- **Layout**: Linear backbone cable with drop lines
- **Advantages**: Simple setup, minimal cabling required
- **Disadvantages**: Single point of failure, network performance decreases with more devices

## Network Configuration
- **Total Devices**: 4 PCs, 1 Hub
- **IP Scheme**: 192.168.1.0/24

## Devices Used
- 4 PCs
- 1 Hub
- Coaxial cables

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway |
|--------|------------|-------------|-----------------|
| PC0    | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1    | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| PC2    | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |
| PC3    | 192.168.1.13 | 255.255.255.0 | 192.168.1.1 |

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Complete bus topology layout*

![Device Configuration](./screenshots/device-config.png)
*PC0 IP configuration*

![Connectivity Test](./screenshots/ping-test.png)
*Successful ping test between PC0 and PC3*

## Verification
- ✅ All devices can communicate with each other
- ✅ IP addresses properly assigned and unique
- ✅ No packet collisions detected in simulation
- ✅ End-to-end connectivity verified
