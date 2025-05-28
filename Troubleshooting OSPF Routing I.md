## Objective
Analyze, locate, and correct Open Shortest Path First (OSPF) operation problems in the network. You will be working on SecondFloor and Client1 in this lab.
!!!This lab taught me power and value of the debug command

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator:
![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084249.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084304.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084312.png)

---

## Troubleshooting Steps
### SecondFloor
## Debug
```cisco
debug ip ospf events
```
![debug](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084641.png)

---

## Verification
```cisco
show ip ospf neighbor
show ip ospf database
show ip ospf interface s0/0
show ip interface brief
show ip route
show ip protocols
```
![verification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20083856.png)
![verification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20083936.png)
![verification 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20083957.png)
![verification 4](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084013.png)
![verification 5](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084028.png)
![verification 6](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084041.png)

---

## Fix
```cisco
conf t
router ospf 1
no network 10.28.0.8 0.0.0.3 area 0
network 10.28.0.8 0.0.0.3 area 2 
```
![fix](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-28%20084230.png)
