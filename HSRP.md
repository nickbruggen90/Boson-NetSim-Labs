## Objective
In this lab, you will configure interface tracking in a Hot Standby Router Protocol (HSRP) environment. HSRP is a network protocol that can be used to ensure the immediate and transparent recovery of traffic clients from first-hop failures in network edge devices by providing network redundancy for IP networks. Interface tracking enables HSRP to monitor a given interface and automatically adjust the HSRP priority of a device when that interface goes down or comes up.

---

# Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20110055.png)
![connections chart](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20110110.png)

---

## Configuration Steps
### DSW2
```cisco
en
conf t
interface vlan 1
standby 1 track f0/1 9
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20110138.png)

---

## Verification
```cisco
show standby
```
![DSW2 verification](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20110146.png)
