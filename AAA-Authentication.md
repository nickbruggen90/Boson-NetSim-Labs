## Objective
Configure P1R1 to use a Terminal Access Controller Access Control System Plus (TACACS+) server to authenticate P1R2 as it attempts to establish a Point-to-Point Protocol (PPP) connection with Password Authentication Protocol (PAP) authentication across the serial link.  

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. The TACACS+ server is located on the Ethernet backbone at 10.2.2.200.For this lab, you will be responsible for configuring P1R1 and P1R2. 
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20073130.png)

--

## Configuration Steps

### P1R1
```cisco
en
conf t
interface serial 0/1
ip address 10.1.1.1 255.255.255.0
encapsulation hdlc
clock rate 1000000
do ping 10.2.2.200 (pinging tacacs+ server)
exit
router rip
version 2
network 10.0.0.0
exit
aaa new-model
tacacs timeout 15
tacacs host 10.2.2.200
tacacs key cisco
aaa authentication ppp AAALab tacacs local
interface serial 0/1
shutdown
encapsulation ppp
ppp pap sent-username P1R1 password cisco
ppp authentication pap AAALab
```
![P1R1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20073142.png)

### P1R2
```cisco
en
conf t
interface serial 0/0
ip address 10.1.1.2 255.255.255.0
exit
router rip
version 2
network 10.0.0.0
exit
interface serial 0/0
encapsulation ppp
ppp pap sent-username AAALab password cisco
ppp authentication pap
exit
username P1R1 password cisco
interface serial 0/0
shutdown
no shutdown
```
![P1R2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20073151.png)

---

