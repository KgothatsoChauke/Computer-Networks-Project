# Ring Topology

## Overview
Devices connected in a circular data path with unidirectional/bidirectional flow.

## Characteristics
- **Layout**: Closed loop configuration
- **Advantages**: Equal network access, orderly network access, performs better than bus under heavy load
- **Disadvantages**: Single break disrupts entire network, difficult to troubleshoot, adding devices disrupts network

## Network Configuration
- **Total Devices**: [e.g., 6 PCs, 6 switches in ring]
- **IP Scheme**: [e.g., 192.168.1.0/24]
- **Data Flow**: [Unidirectional/Bidirectional]
- **Access Method**: [Token passing / Specify other]

## Devices Used
- [Number] PCs
- [Number] Switches/Routers in ring formation
- [Any MAU if used]

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway | Ring Position |
|--------|------------|-------------|-----------------|--------------|
| [PC0] | [192.168.1.10] | [255.255.255.0] | [192.168.1.1] | [Between Switch0 and Switch1] |
| [PC1] | [192.168.1.11] | [255.255.255.0] | [192.168.1.1] | [Between Switch1 and Switch2] |
| [Add all devices] | | | | |

## Configuration Notes
- Ring direction: [Clockwise/Counter-clockwise/Bidirectional]
- Token rotation time: [If applicable]
- Fault tolerance mechanisms: [Dual ring / Specify if used]

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Ring network layout*

![Device Configuration](./screenshots/device-config.png)
*Device and ring interface settings*

![Token Passing](./screenshots/ping-test.png)
*Data transmission in ring*

## Verification
- ✅ Circular connectivity confirmed
- ✅ Data flows in [direction] direction
- ✅ Network access is orderly
- ✅ Break simulation shows network vulnerability
