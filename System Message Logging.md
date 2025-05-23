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
em
conf t
logging 10.1.0.10
logging trap 4
do show logging
```
### Switch2
```cisco
en
conf t
logging 10.1.0.10
logging trap 4
do show logging
```
![switch1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20042745.png)
![switch2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20042840.png)

---

## Verification
### Router1 / Switch1 / Switch2
```cisco
en
show logging
```

### Verification Output
![switch1_verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20042759.png)
![switch2_verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20042903.png)

