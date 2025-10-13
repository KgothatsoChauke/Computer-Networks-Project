# Mesh Topology

## Overview
[Full/Partial] mesh topology with point-to-point connections between devices.

## Characteristics
- **Layout**: [Full mesh: all devices connected to all others] / [Partial mesh: selective connections]
- **Advantages**: High redundancy, fault tolerance, high performance
- **Disadvantages**: High cabling cost, complex installation and maintenance

## Network Configuration
- **Total Devices**: [e.g., 4 PCs, 4 switches]
- **IP Scheme**: [e.g., 10.0.0.0/24, 10.0.1.0/24, etc.]
- **Mesh Type**: [Full/Partial]
- **Total Connections**: [e.g., 6 direct connections]

## Devices Used
- [Number] PCs
- [Number] Switches/Routers

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway | Connected To |
|--------|------------|-------------|-----------------|-------------|
| [PC0] | [10.0.0.10] | [255.255.255.0] | [10.0.0.1] | [PC1, PC2, PC3] |
| [PC1] | [10.0.1.10] | [255.255.255.0] | [10.0.1.1] | [PC0, PC2, PC3] |
| [Add all devices with connections] | | | | |

## Configuration Notes
- Each connection uses a separate subnet
- [Number] direct connections established
- Routing protocols: [Static/Dynamic - specify if used]

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Mesh network layout showing all connections*

![Device Configuration](./screenshots/device-config.png)
*Interface configurations*

![Redundancy Test](./screenshots/ping-test.png)
*Connectivity after simulating link failure*

## Verification
- ✅ Multiple paths between all devices
- ✅ Fault tolerance tested by disabling links
- ✅ All direct connections operational
- ✅ No single point of failure
