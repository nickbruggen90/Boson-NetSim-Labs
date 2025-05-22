## Objective
Configure Virtual Router Redundancy Protocol (VRRP), and verify the configuration.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. For this lab, your network design includes four switches: ASW1, ASW2, DSW1, and DSW2. ASW1 and ASW2 are Layer 2 switches, and DSW1 and DSW2 are Layer 3 switches. DSW1 and DSW2 will be referred to as routers throughout the lab. Layer 3 switches are capable of transmitting data at Layer 2 switch speeds but can also determine for themselves how traffic should flow at Layer 3.
![topology pic](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20115832.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20115847.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20115853.png)

---
## Configuration Steps
### DSW1
```cisco
en
conf t
interface vlan 100
vrrp 100 ip 10.10.100.1
vrrp 100 priority 120
exit
interface vlan 200
vrrp 200 ip 10.10.200.1
vrrp 200 priority 90
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20120246.png)

### DSW2
```cisco
en
conf t
interface vlan 100
vrrp 100 ip 10.10.100.1
vrrp 100 priority 90
exit
interface vlan 200
vrrp 200 ip 10.10.200
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20120258.png)

### ASW1
```cisco
en
conf t
ip default-gateway 10.10.100.1
```
![ASW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20120306.png)

### ASW2
```cisco
en
conf t
ip default-gateway 10.10.100.1
```
![ASW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20120313.png)

### Client(s)
```cisco
ipconfig /dg 10.10.100.1
ipconfig /dg 10.10.200.1
```
![clients commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20120319.png)

---

## Verification
```cisco
show vrrp
```
![DSW1 verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20120400.png)
![DSW2 verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20120416.png)

