## Objective
In this lab, you will configure Hot Standby Router Protocol (HSRP) and interface tracking. HSRP is a network protocol that can be used to ensure the immediate and transparent recovery of client traffic from first-hop failures in network edge devices by providing network redundancy for IP networks. Interface tracking enables HSRP to monitor a given interface and to automatically adjust the HSRP priority of a device when that interface goes down or comes up.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.

![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20111510.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20111518.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20111531.png)
![connections chart 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20111538.png)

---

## Configuration Steps
### DSW1
```cisco
en
conf t
interface vlan 100
standby 100 priority 110
standby 100 ip 10.10.100.1
standby 100 preempt
standby 100 track f0/1 1
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20112352.png)

### DSW2
```cisco
en
conf t
interface vlan 100
standby 100 priority 109
standby 100 ip 10.10.100.1
standby 100 preempt
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20112406.png)

### ASW1
```cisco
en
conf t
ip default-gateway 10.10.100.1
```
![ASW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20112417.png)

### ASW2
```cisco
en
conf t
ip default-gateway 10.10.100.1
```
![ASW2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20112427.png)

---

## Verification
```cisco
show standby
```
![DSW1 verification](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20112608.png)
