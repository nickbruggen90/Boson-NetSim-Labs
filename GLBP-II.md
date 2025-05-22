## Objective
In this lab, you will configure and verify a basic Gateway Load Balancing Protocol (GLBP) environment. GLBP is a First-Hop Redundancy Protocol (FHRP) that can be used to ensure the immediate and transparent recovery from first-hop failures in network edge devices by providing gateway redundancy for IP networks. You will also configure GLBP authentication.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator:
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141141.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141205.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141211.png)

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
glbp 10 authentication text my80$0nL485
glbp 10 authentication md5 key-string my80$0nL485
```
![R1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141655.png)

### R2
```cisco
en
conf t
interface e0/3
glbp 10 ip 10.10.10.25
glbp 10 authentication text my80$0nL485
glbp 10 authentication md5 key-string my80$0nL485
```
![R2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141707.png)

### R3
```cisco
en
conf t
interface e0/3
glbp 10 ip 10.10.10.25
glbp 10 authentication text my80$0nL485
glbp 10 authentication md5 key-string my80$0nL485
```
![R3 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141715.png)

---

## Verification
```cisco
show glbp
show glbp brief
```
![R1 verification 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141733.png)
![R1 verification 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20141746.png)
