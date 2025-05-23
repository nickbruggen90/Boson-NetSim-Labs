## Objective
Configure DSW switches for routing, and re-address the network for routing. For this lab, you will be responsible for configuring all four switches. P1PC1 and P2PC2 are PC workstations. P1ASW1 and P2ASW2 are Access layer switches. P1DSW1 and P2DSW2 are Distribution layer switches. The Access and Distribution layers are two of the three layers in the Cisco three-layer hierarchical network model, which also includes the Core layer.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator:

![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20115830.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20120229.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20120239.png)
![connections chart 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20120245.png)

--

## Configuration Steps
### P1ASW1
```cisco
en
conf t
interface vlan 1
ip address 172.16.1.10 255.255.255.0
exit
ip default-gateway 172.16.1.100
exit
ping 172.16.1.100
```
![P1ASW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20115841.png)

### P1DSW1
```cisco
en
conf t
interface vlan 1
ip address 172.16.1.100 255.255.255.0
interface vlan 11
ip address 172.16.11.100 255.255.255.0
exit
ip routing
router eigrp 100
network 172.16.0.0 0.0.255.255
```
![P1DSW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20115852.png)

### P2ASW2
```cisco
en
conf t
interface vlan 1
ip address 172.16.1.20 255.255.255.0
exit
ip default-gateway 172.16.1.200
exit
ping 172.16.1.200
```
![P2ASW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20115900.png)

### P2DSW2
```cisco
en
conf t
interface vlan 1
ip address 172.16.1.200 255.255.255.0
interface vlan 12
ip address 172.16.12.200 255.255.255.0
exit
ip routing
router eigrp 100
network 172.16.0.0 0.0.255.255
```
![P2DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20115910.png)

---

## Verification
```cisco
show ip route
show ip protocols
show ip interface brief
```
![verification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20120029.png)
![verification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20120059.png)
![verification 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20120118.png)
