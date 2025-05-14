## Objective  
Learn how to configure and verify system message logging.  

---

## Lab Topology  
The topology diagram below represents the NetMap in the Simulator.  
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20042538.png)

---

## Configuration Steps
### Router1
```cisco
en
conf t
logging 10.1.0.10
logging trap 4
do show logging
```
### Switch1
```cisco
logging 10.1.0.10
logging trap 4
do show logging
```
### Switch2
```cisco
logging 10.1.0.10
logging trap 4
do show logging
```
