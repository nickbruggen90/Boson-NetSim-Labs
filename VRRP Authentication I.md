## Objective
In this lab, you will configure a Virtual Router Redundancy Protocol (VRRP) environment and VRRP authentication. VRRP is a network protocol that can be used to ensure the immediate and transparent recovery from first-hop failures in network edge devices by providing network redundancy for IP networks.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. The VRRP routers in this topology are Layer 3 switches that will be referred to as routers throughout the lab. Layer 3 switches are capable of transmitting data at Layer 2 switch speeds but can also determine for themselves how traffic should flow at Layer 3.

![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20081940.png)

![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20081957.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20082005.png)

---

## Configuration Steps
### DSW1
```cisco
en
conf t
interface vlan 2
vrrp 2 preempt
vrrp 2 authentication text 80$0nL48
vrrp 2 ip 10.10.2.3
no vrrp 2 authentication text 80$0nL48
vrrp 2 authentication md5 key-string my80$0nL485
```
![DSW1 commands][(https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20082021.png)

### DSW2
```cisco
en
conf t
interface vlan 2
vrrp 2 priority 110
vrrp 2 preempt
vrp 2 ip 10.10.2.3
vrrp 2 authentication text 80$0nL48
no vrrp 2 authentication text 80$0nL48
vrrp 2 authentication md5 key-string my80$0nL485
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20082033.png)

---

## Verification
```cisco
show vrrp
```
![verification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20082042.png)
![verification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20082051.png)
