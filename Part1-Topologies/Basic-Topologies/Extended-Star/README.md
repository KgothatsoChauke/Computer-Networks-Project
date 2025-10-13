# Extended Star Topology

## Overview
Hierarchical star topology with a central core switch connecting multiple access layer switches, each forming their own star networks with end devices in a cross formation.

## Characteristics
- **Layout**: Multi-level hierarchical star with central core switch and peripheral access switches in cross formation
- **Advantages**: Scalable, easy to manage sections, fault isolation at multiple levels, modular design
- **Disadvantages**: Complex cabling, multiple potential points of failure, requires more infrastructure

## Network Configuration
- **Total Devices**: 6 PCs, 6 Laptops, 5 Switches
- **IP Scheme**: 192.168.1.0/24
- **Topology**: Two-level hierarchical star
- **Central Core**: Switch3 as backbone device
- **Access Layer**: 4 switches forming individual star networks

## Devices Used
- 6 PCs (PC0, PC1, PC2, PC3, PC4, PC5)
- 6 Laptops (Laptop0, Laptop1, Laptop2, Laptop3, Laptop4, Laptop5)
- 5 Switches (Switch0, Switch1, Switch2, Switch3, Switch4)

## Network Hierarchy
**Core Layer:**
- Switch3 (Central backbone switch)

**Access Layer:**
- Switch1 (Top) - Connects laptops 3,4,5
- Switch2 (Right) - Connects PCs 3,4,5  
- Switch0 (Bottom) - Connects laptops 0,1,2
- Switch4 (Left) - Connects PCs 0,1,2

## IP Address Table

### Switch4 (Left) - PC Star
| Device | IP Address | Subnet Mask | Default Gateway | Connected Port |
|--------|------------|-------------|-----------------|---------------|
| PC0 | 192.168.1.1 | 255.255.255.0 | 192.168.1.254 | Switch4 Fa0/1 |
| PC1 | 192.168.1.2 | 255.255.255.0 | 192.168.1.254 | Switch4 Fa0/2 |
| PC2 | 192.168.1.3 | 255.255.255.0 | 192.168.1.254 | Switch4 Fa0/3 |

### Switch0 (Bottom) - Laptop Star
| Device | IP Address | Subnet Mask | Default Gateway | Connected Port |
|--------|------------|-------------|-----------------|---------------|
| Laptop0 | 192.168.1.4 | 255.255.255.0 | 192.168.1.254 | Switch0 Fa0/1 |
| Laptop1 | 192.168.1.5 | 255.255.255.0 | 192.168.1.254 | Switch0 Fa0/2 |
| Laptop2 | 192.168.1.6 | 255.255.255.0 | 192.168.1.254 | Switch0 Fa0/3 |

### Switch2 (Right) - PC Star
| Device | IP Address | Subnet Mask | Default Gateway | Connected Port |
|--------|------------|-------------|-----------------|---------------|
| PC3 | 192.168.1.7 | 255.255.255.0 | 192.168.1.254 | Switch2 Fa0/1 |
| PC4 | 192.168.1.8 | 255.255.255.0 | 192.168.1.254 | Switch2 Fa0/2 |
| PC5 | 192.168.1.9 | 255.255.255.0 | 192.168.1.254 | Switch2 Fa0/3 |

### Switch1 (Top) - Laptop Star
| Device | IP Address | Subnet Mask | Default Gateway | Connected Port |
|--------|------------|-------------|-----------------|---------------|
| Laptop3 | 192.168.1.10 | 255.255.255.0 | 192.168.1.254 | Switch1 Fa0/1 |
| Laptop4 | 192.168.1.11 | 255.255.255.0 | 192.168.1.254 | Switch1 Fa0/2 |
| Laptop5 | 192.168.1.12 | 255.255.255.0 | 192.168.1.254 | Switch1 Fa0/3 |

## Switch Interconnection
| Core Switch | Port | Connected To | Direction |
|-------------|------|-------------|-----------|
| Switch3 | Fa0/1 | Switch1 | Up |
| Switch3 | Fa0/2 | Switch2 | Right |
| Switch3 | Fa0/3 | Switch0 | Down |
| Switch3 | Fa0/4 | Switch4 | Left |

## Configuration Notes
- All devices in single broadcast domain (192.168.1.0/24)
- Core switch (Switch3) acts as network backbone in cross formation
- Each access switch forms independent star network
- Switch-to-switch connections use crossover cables
- End device connections use straight-through cables
- Default gateway reserved as 192.168.1.254

## Network Segmentation
- **Physical Segments**: 5 (4 access stars + 1 core)
- **Logical Network**: Single IP subnet
- **Collision Domains**: Multiple (one per switch port)
- **Broadcast Domain**: Single (unless VLANs implemented)

## Traffic Flow Analysis
- **Intra-star communication**: Local to access switch (fastest)
- **Inter-star communication**: Through core switch (2-hop path)
- **Maximum Hops**: 3 (end device → access switch → core switch → access switch → end device)

## IP Address Grouping Logic
- **Left Star (Switch4)**: PCs 0,1,2 → IPs .1,.2,.3
- **Bottom Star (Switch0)**: Laptops 0,1,2 → IPs .4,.5,.6
- **Right Star (Switch2)**: PCs 3,4,5 → IPs .7,.8,.9
- **Top Star (Switch1)**: Laptops 3,4,5 → IPs .10,.11,.12

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Extended star showing cross formation with central Switch3*

![Core Switch Configuration](./screenshots/core-config.png)
*Switch3 configuration showing 4 connections to access switches*

![Access Switch Example](./screenshots/access-config.png)
*Sample access switch configuration*

![Cross-star Communication](./screenshots/ping-test.png)
*Connectivity test between devices on different access switches*

## Verification Tests
- ✅ All devices within same access star can communicate
- ✅ Cross-star communication working (PC0 to PC3 through core)
- ✅ Core switch failure isolates all access stars
- ✅ Individual access switch failure only affects its local devices
- ✅ IP address assignment follows logical grouping
- ✅ Hierarchical fault isolation demonstrated

## Advantages Demonstrated
- **Modularity**: Easy to add new access stars
- **Fault Isolation**: Problems contained within access stars
- **Scalability**: Can add more access switches to core
- **Manageability**: Sectional troubleshooting possible

## Performance Characteristics
- **Local Traffic**: Optimal (stays within access switch)
- **Cross-star Traffic**: Slight latency through core
- **Core Load**: Manages inter-star communication only
- **Scalability**: High - easy to expand access layer
