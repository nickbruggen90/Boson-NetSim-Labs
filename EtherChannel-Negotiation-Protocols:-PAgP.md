## Objective
You will plan, implement, and verify Layer 2 EtherChannel configurations in this lab by configuring EtherChannel between two switches using the Port Aggregation Protocol (PAgP) negotiation protocol.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology pic](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20125438.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20125500.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20125509.png)
![connections chart 3](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20125517.png)
![connections chart 4](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20125536.png)

---

## Configuration Steps
### DSW1
```cisco
en
conf t
interface range f0/5 - 6
channel-protocol pagp
channel-group 1 mode auto
interface port-channel 1
switchport trunk encapsulation dot1q
switchport mode trunk
interface range f0/5 - 6
channel-group 1 mode desirable
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20125842.png)

### DSW2
```cisco
en
conf t
interface range f0/5 - 6
channel-protocol pagp
channel-group 1 mode auto
interface port-channel 1
switchport trunk encapsulation dot1q
switchport mode trunk
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20125850.png)

---

## Verification
```cisco
show interfaces port-channel 1
show interfaces port-channel 1 trunk
show interfaces port-channel 1 status
show interfaces port-channel 1 switchport
show interfaces switchport
show interfaces status
show interfaces trunk
show interfaces f0/5
```
![DSW1 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20130048.png)
![DSW1 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20130124.png)
![DSW1 3](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20130154.png)
![DSW1 4](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20130215.png)
![DSW1 5](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20130235.png)
![DSW1 6](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20130253.png)
