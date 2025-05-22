## Objective
Configure two Hot Standby Router Protocol (HSRP) groups, and verify the configuration.

---

## Lab Topology
For this lab, your network design will include four switches, ASW1, ASW2, DSW1, and DSW2. Each switch is connected to one another by an Ethernet link. ASW1 and ASW2 are access layer switches, and DSW1 and DSW2 are distribution layer switches. Two PCs named Client1 and Client2 are connected to the access layer switches on FastEthernet port 0/3. Even though there are only two access layer switches in the network design, each client represents a group of workstations. Since each group of workstations generates a significant amount of traffic, you want to route each group through a different switch but still provide a redundant default gateway for them in the unlikely event one of the switches fails. Upon the initial loading of the lab, all devices will be configured with the IP addresses, virtual LANs (VLANs), and Spanning Tree commands needed for connectivity.
	
The topology diagram below represents the NetMap in the Simulator:
![topology pic](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073004.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073013.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073020.png)

---

## Configuration Steps
### DSW1
```cisco
en
conf t
interface vlan 1
standby 10 ip 172.16.3.252
standby 10 priority 120
standby 20 ip 172.16.3.254
standby 20 priority 90
standby 10 preempt
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073610.png)

### DSW2
```cisco
en
conf t
interface vlan 1
standby 10 ip 172.16.3.252
standby 10 priority 90
standby 20 ip 172.16.3.254
standby 20 priority 120
standby 10 preempt
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073618.png)

---
## Verification
```cisco
show standby
show standby brief
```
![DSW1 verification 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073651.png)
![DSW1 verification 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073702.png)
![DSW2 verification 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073715.png)
![DSW2 verification 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20073725.png)

##
