# Bus Topology

## Overview
A bus network topology where all switches are connected in a linear backbone, with each switch serving one PC device.

## Characteristics
- **Layout**: Linear bus of switches with individual PC connections
- **Advantages**: Simple setup, minimal backbone cabling, easy to understand
- **Disadvantages**: Single point of failure in backbone, performance degrades with heavy traffic, entire network affected if backbone breaks

## Network Configuration
- **Total Devices**: 9 PCs, 8 Switches
- **IP Scheme**: 192.168.1.0/24
- **Backbone Type**: Linear switch connections
- **PC Connections**: Individual switch connections

## Devices Used
- 9 PCs (PC0 through PC8)
- 8 Switches (Switch1 through Switch8)
- Straight-through Ethernet cables

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway | Connected Switch |
|--------|------------|-------------|-----------------|------------------|
| PC0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 | Switch1 |
| PC1 | 192.168.1.3 | 255.255.255.0 | 192.168.1.1 | Switch2 |
| PC2 | 192.168.1.4 | 255.255.255.0 | 192.168.1.1 | Switch3 |
| PC3 | 192.168.1.5 | 255.255.255.0 | 192.168.1.1 | Switch4 |
| PC4 | 192.168.1.6 | 255.255.255.0 | 192.168.1.1 | Switch5 |
| PC5 | 192.168.1.7 | 255.255.255.0 | 192.168.1.1 | Switch6 |
| PC6 | 192.168.1.8 | 255.255.255.0 | 192.168.1.1 | Switch7 |
| PC7 | 192.168.1.9 | 255.255.255.0 | 192.168.1.1 | Switch8 |
| PC8 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 | Switch8 (if daisy-chained) |

## Switch Connection Table
| Switch | Connected To Left | Connected To Right | Connected PC |
|--------|------------------|-------------------|-------------|
| Switch1 | N/A (Start) | Switch2 | PC0 |
| Switch2 | Switch1 | Switch3 | PC1 |
| Switch3 | Switch2 | Switch4 | PC2 |
| Switch4 | Switch3 | Switch5 | PC3 |
| Switch5 | Switch4 | Switch6 | PC4 |
| Switch6 | Switch5 | Switch7 | PC5 |
| Switch7 | Switch6 | Switch8 | PC6 |
| Switch8 | Switch7 | N/A (End) | PC7, PC8 |

## Configuration Notes
- All devices share the same broadcast domain (192.168.1.0/24)
- No VLAN configuration - single flat network
- Switches forward frames based on MAC address learning
- Default gateway set to 192.168.1.1 for future router expansion
- Each switch has one PC device connected (except Switch8 which may have two)

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Complete bus topology with 8 switches in linear backbone*

![Device Configuration](./screenshots/device-config.png)
*PC0 IP configuration example*

![Connectivity Test](./screenshots/ping-test.png)
*Successful ping test between end devices (PC0 to PC8)*

## Verification Tests
- ✅ PC0 can ping PC8 (end-to-end connectivity)
- ✅ All intermediate PCs can communicate
- ✅ No IP address conflicts detected
- ✅ Broadcast traffic reaches all devices
- ✅ Switch forwarding tables properly learned MAC addresses

## Performance Notes
- Increased latency for communication between distant devices
- Bandwidth shared across the backbone
- Single break in backbone cable would segment the network
