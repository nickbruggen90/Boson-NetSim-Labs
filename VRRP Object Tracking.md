## Objective
In this lab, you will configure a Virtual Router Redundancy Protocol (VRRP) environment and VRRP object tracking. VRRP is a First Hop Redundancy Protocol (FHRP) that can be used to ensure the immediate and transparent recovery from first-hop failures in network edge devices by providing gateway redundancy for IP networks. Object tracking enables a VRRP Backup router to take over for a VRRP Master router when a specific event occurs, such as when the line protocol on an external network-facing interface enters the down state.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. The VRRP routers in this topology are Layer 3 switches that will be referred to as routers throughout the lab. Layer 3 switches are capable of transmitting data at Layer 2 switch speeds but can also determine for themselves how traffic should flow at Layer 3.
![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20072107.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20072115.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20072131.png)

---

## Configuration Steps
### DSW2
```cisco
en
conf t
interface vlan 2
vrrp 2 priority 110
vrrp 2 ip 10.10.2.3
exit
track 1 interface f0/1 line-protocol
exit
interface vlan 2
vrrp 2 track 1 decrement 10
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20072159.png)

### DSW1
```cisco
en
conf t
interface vlan 2
vrrp 2 ip 10.10.2.3
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20072210.png)

---

## Verification
```cisco
show vrrp
```
![verification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20072218.png)
![verification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20072226.png)
