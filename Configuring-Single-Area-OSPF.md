## Objective
Configure the network to use Open Shortest Path First (OSPF) for a single area. All OSPF routers will be in Area 0.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. Configure the devices in Pod 1; Pod 2 has already been configured upon the initial loading of the lab.

![topology pic](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081340.png)
![connections chart](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081444.png)

---

## Configuration Steps:
### P1R1
```cisco
en
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
```
![P1R1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081659.png)

### P1R2
```cisco
en
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
```
![P1R2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081710.png)

### P1R3
```cisco
en
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
```
![P1R3 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081721.png)

---

### Verification
```cisco
show ip ospf
show ip ospf database
show ip ospf neighbor
show ip protocols
show ip ospf interface f0/0
```
![P1R3 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081827.png)
![P1R3 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081849.png)
![P1R3 3](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081911.png)
![P1R3 4](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20081955.png)
![P1R3 5](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20082019.png)
