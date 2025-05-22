## Objective
Configure Hot Standby Router Protocol (HSRP), and verify the configuration. HSRP is a network protocol that can be used to ensure the immediate and transparent recovery of traffic clients from first-hop failures in network edge devices by providing network redundancy for IP networks.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. For this lab, your network design includes four switches: ASW1, ASW2, DSW1, and DSW2. The switches are connected to one another by Ethernet links. ASW1 and ASW2 are access layer switches, and DSW1 and DSW2 are distribution layer switches. Two workstations, named Client1 and Client2, are connected to the access layer switches on FastEthernet port 0/3.

![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20063226.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20063720.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20063730.png)

---

## Configuration Steps
### DSW1
```cisco
en
conf t
interface vlan 1
standby 3 ip 172.16.3.1
standby 3 priority 90
standby 3 preempt
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20063552.png)

### DSW2
```cisco
en
conf t
interface vlan 1
standby 3 ip 172.16.3.1
standby 3 priority 120
standby 3 preempt
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20063603.png)

---

## Verification
```cisco
show standby
show standby brief
```
![verification 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20063622.png)
![verification 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20063639.png)

