# Network Troubleshooting Project - Presentation Ready

## Quick Start - Presentation Commands

### ⚡  TROUBLESHOOTING COMMANDS

#### **Issue 1: VLAN Misconfiguration - PC3 Cannot Communicate**
**Symptoms:** PC3 (192.168.20.10) unreachable from all devices

**Diagnostic Commands:**
```bash
# Check VLAN assignments
show vlan brief

# Verify port configuration
show interfaces fastethernet0/1 switchport

# Check MAC address learning
show mac address-table interface fastethernet0/1
```
**Fix Command:**
```bash
configure terminal
interface fastethernet0/1
switchport access vlan 20
end
write memory
```
**Verification:**
```bash
# From Laptop:
ping 192.168.20.10

# Check VLAN is fixed:
show vlan brief
```

---

#### **Issue 2: OSPF Failure - Inter-VLAN Routing Broken**
**Symptoms:** Devices in VLAN 20 cannot reach VLAN 10

**Diagnostic Commands:**
```bash
# Check OSPF neighbors
show ip ospf neighbor

# Verify routing table
show ip route

# Check specific route
show ip route 192.168.10.0
```
**Fix Command (if OSPF is down):**
```bash
configure terminal
router ospf 1
network 10.0.12.0 0.0.0.3 area 0
network 10.0.23.0 0.0.0.3 area 0
end
write memory
```
**Verification:**
```bash
show ip ospf neighbor
ping 192.168.10.10
```

---

#### **Issue 3: ACL Blocking Traffic**
**Symptoms:** Specific traffic patterns failing

**Diagnostic Commands:**
```bash
# Check ACL configuration
show access-lists

# Verify ACL application
show running-config interface gigabitethernet0/0.20
```
**Fix Command:**
```bash
configure terminal
interface gigabitethernet0/0.20
no ip access-group 100 out
exit
no access-list 100
end
write memory
```

---

## 🎯 PRESENTATION TROUBLESHOOTING SCENARIOS

### **Scenario 1: The Isolated PC**
**Problem:** PC3 cannot communicate with anyone

**Step-by-Step Troubleshooting:**
```bash
# Test Basic Connectivity
ping 192.168.20.10

# Check Local Network
ping 192.168.20.1

# Investigate VLAN Configuration
show vlan brief

# Verify Port Settings
show interfaces fastethernet0/1 switchport

# Apply Fix
configure terminal
interface fastethernet0/1
switchport access vlan 20
end
write memory

# Verify Resolution
ping 192.168.20.10
show vlan brief
```

---

### **Scenario 2: Inter-VLAN Routing Failure**
**Problem:** VLAN 20 devices cannot reach VLAN 10

**Step-by-Step Troubleshooting:**
```bash
# Test Cross-VLAN Connectivity
ping 192.168.10.10
tracert 192.168.10.10

# Check Routing Table
show ip route

# Verify OSPF Status
show ip ospf neighbor
show ip ospf interface

# Check Router Interfaces
show ip interface brief

# Apply OSPF Fix if Needed
configure terminal
router ospf 1
no shutdown
end
write memory
```

---

## 📋 QUICK REFERENCE COMMANDS

### **Basic Connectivity Tests**
```bash
# Test local connectivity
ping 192.168.20.1

# Test cross-VLAN connectivity  
ping 192.168.10.10

# Trace the path
tracert 192.168.10.10

# Check local IP configuration
ipconfig
```

### **Switch Diagnostic Commands**
```bash
# VLAN information
show vlan brief

# Trunk status
show interfaces trunk

# Port configuration
show interfaces fastethernet0/1 switchport

# MAC address table
show mac address-table

# Interface status
show interfaces status
```

### **Router Diagnostic Commands**
```bash
# Routing table
show ip route

# OSPF information
show ip ospf neighbor
show ip ospf interface

# Interface status
show ip interface brief

# ACL information
show access-lists
```

---

## 🛠️ NETWORK BUILD COMMANDS (For Reference)

### **Switch1 Configuration**
```bash
enable
configure terminal
vlan 10
 name STAFF_WIRED
vlan 20
 name GUEST_WIRED
vlan 99
 name NATIVE
exit

interface fastethernet0/1
 switchport mode access
 switchport access vlan 10
 no shutdown

interface fastethernet0/2
 switchport mode access
 switchport access vlan 10
 no shutdown

interface fastethernet0/23
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20
 no shutdown

interface fastethernet0/24
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40
 no shutdown

exit
write memory
```

### **R1 Router Configuration**
```bash
enable
configure terminal
interface gigabitethernet0/0
 no ip address
 no shutdown

interface gigabitethernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
 no shutdown

interface gigabitethernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
 no shutdown

interface gigabitethernet0/1
 ip address 10.0.12.1 255.255.255.252
 no shutdown

router ospf 1
 network 192.168.10.0 0.0.0.255 area 0
 network 192.168.20.0 0.0.0.255 area 0
 network 10.0.12.0 0.0.0.3 area 0

exit
write memory
```

---

## ✅ FUNCTIONALITY CHECKLIST

### **Pre-Troubleshooting Verification**
- All devices can ping their default gateways
- Inter-VLAN routing working
- OSPF neighbors established
- All switch ports operational

### **Post-Fix Verification**
- PC3 can communicate with all devices
- VLAN assignments correct
- No packet loss in pings
- Routing tables populated correctly
