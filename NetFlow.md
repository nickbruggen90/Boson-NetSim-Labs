## Objective  
In this lab, you will learn the basic commands to configure NetFlow on a Cisco router and to verify an existing NetFlow configuration.  

---

## Lab Topology  
The topology diagram below represents the NetMap in the Simulator.  
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20045615.png)

---

## Configuration Steps

### Router 1
```cisco
en
conf t
interface f0/0
ip flow ingress
interface f0/1
ip flow egress
exit
ip flow version 9
ip flow destination 1.2.3.4 9999
ip flow destination 4.3.2.1 8888 sctp
```
![router1_commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20045412.png)

---

## Verification

### Router1
```cisco
en
show ip flow interface
show ip flow export
show ip cache flow
```

![router1_verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20045449.png)
![router1_verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20045510.png)
![router1_verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20045539.png)

