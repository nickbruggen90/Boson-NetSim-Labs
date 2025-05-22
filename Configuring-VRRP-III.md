## Objective
Configure Virtual Router Redundancy Protocol (VRRP), and verify the configuration.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. For this lab, your network design includes four switches: ASW1, ASW2, DSW1, and DSW2. ASW1 and ASW2 are Layer 2 switches, and DSW1 and DSW2 are Layer 3 switches. DSW1 and DSW2 will be referred to as routers throughout the lab. Layer 3 switches are capable of transmitting data at Layer 2 switch speeds but can also determine for themselves how traffic should flow at Layer 3.
![topology pic](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20124409.png)

![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20124418.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20124425.png)

---

## Configuration Steps
### DSW2
```cisco
en
conf t
track 1 interface f0/1 line-protocol
interface vlan 200
vrrp 2 ip 10.10.200.1
vrrp 2 track 1 decrement 145
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20124628.png)

### DSW1
```cisco
en
conf t
interface vlan 200
vrrp 2 ip 10.10.200.1
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20124635.png)

---

## Verification
```cisco
show vrrp
```
![DSW2 verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20124716.png)
