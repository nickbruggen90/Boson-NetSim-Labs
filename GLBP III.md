## Objective
In this lab, you will configure and verify Gateway Load Balancing Protocol (GLBP) environment object tracking and authentication. GLBP is a First-Hop Redundancy Protocol (FHRP) that can be used to ensure the immediate and transparent recovery from first-hop failures in network edge devices by providing gateway redundancy for IP networks. You will also configure GLBP object tracking.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator:

![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20144255.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20144306.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20144314.png)

---

## Configuration Steps
### R1
```cisco
en
conf t
interface e0/3
glbp 10 priority 110
glbp 10 preempt
glbp 10 ip 10.10.10.25
glbp 10 weighting 100 lower 91 upper 100
```
![R1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145041.png)

### R2
```cisco
en
conf t
interface e0/3
glbp 10 ip 10.10.10.25
```
![R2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145052.png)

### R3
```cisco
en
conf t
interface e0/3
glbp 10 ip 10.10.10.25
```
![R3 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145101.png)

---

## Verification
```cisco
show glbp
show glbp brief
```
![R1 verification 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145133.png)
![R1 verification 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145148.png)
