## Objective
In this lab, you will configure a Hot Standby Router Protocol (HSRP) environment and HSRP authentication. HSRP is a network protocol that can be used to ensure the immediate and transparent recovery from first-hop failures in network edge devices by providing network redundancy for IP networks. Authentication protects the specified HSRP group against HSRP spoofing attacks, which can result in a Denial of Service (DoS) condition.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. The HSRP routers in this topology are Layer 3 switches that will be referred to as routers throughout the lab. Layer 3 switches are capable of transmitting data at Layer 2 switch speeds but can also determine for themselves how traffic should flow at Layer 3.
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145911.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145922.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20145936.png)

---

## Configuration Steps
### DSW1
```cisco
en
conf t
interface vlan 100
standby 100 priority 120
standby 100 track f0/1 20
standby 100 authentication 80$0nL48
standby 100 ip 10.10.100.3
no standby 100 authentication 80$0nL48
standby 100 authentication md5 key-string my80$0nL485
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20150323.png)

### DSW2
```cisco
en
conf t
interface vlan 100
standby 100 priority 110
standby 100 preempt
standby 100 ip 10.10.100.3
standby 100 authentication 80$0nL48
no standby 100 authentication 80$0nL48
standby 100 authentication md5 key-string my80$0nL485
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20150332.png)

---

## Verification
```cisco
show standby
show stanby brief
```
![DSW1 verification 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20150349.png)
![DSW1 verification 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20150358.png)
![DSW2 verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20150433.png)
