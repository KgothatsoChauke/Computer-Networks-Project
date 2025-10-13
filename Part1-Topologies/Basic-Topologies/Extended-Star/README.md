# Extended Star Topology

## Overview
Hierarchical star topology with multiple star networks connected through a central backbone.

## Characteristics
- **Layout**: Multiple star networks connected hierarchically
- **Advantages**: Scalable, manageable sections, fault isolation at multiple levels
- **Disadvantages**: Complex design, multiple points of failure possible

## Network Configuration
- **Total Devices**: [e.g., 8 PCs, 3 Switches, 1 Router]
- **IP Scheme**: [e.g., Multiple subnets: 192.168.1.0/24, 192.168.2.0/24]
- **Hierarchy Levels**: [e.g., 2-level hierarchy]
- **Backbone Device**: [e.g., Core switch or router]

## Devices Used
- [Number] PCs total
- [Number] Edge switches
- [Number] Core switches/routers
- [Number] Hierarchy levels

## IP Address Table
| Device | IP Address | Subnet Mask | Default Gateway | Subnet | Level |
|--------|------------|-------------|-----------------|--------|-------|
| [PC0] | [192.168.1.10] | [255.255.255.0] | [192.168.1.1] | [Subnet A] | [Access] |
| [PC1] | [192.168.2.10] | [255.255.255.0] | [192.168.2.1] | [Subnet B] | [Access] |
| [Core Switch] | [192.168.0.1] | [255.255.255.0] | [N/A] | [Backbone] | [Core] |
| [Add all devices] | | | | | |

## Configuration Notes
- Hierarchy: [Describe levels - e.g., Core, Distribution, Access]
- Inter-switch links: [Trunk ports / Specify configuration]
- Routing: [Static/Dynamic between subnets]
- VLANs: [None / Specify if used]

## Screenshots
![Topology Overview](./screenshots/topology-view.png)
*Extended star hierarchical layout*

![Backbone Configuration](./screenshots/device-config.png)
*Core device configuration*

![Cross-subnet Communication](./screenshots/ping-test.png)
*Inter-subnet connectivity test*

## Verification
- ✅ Intra-subnet communication working
- ✅ Inter-subnet communication through backbone
- ✅ Hierarchical fault isolation demonstrated
- ✅ Scalability for adding new stars confirmed
