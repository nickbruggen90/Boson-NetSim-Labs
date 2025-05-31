## Objective
In this lab, you will learn to use what you know about Layer 2 EtherChannel and Spanning Tree Protocol (STP) to troubleshoot an EtherChannel configuration.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20142038.png)

![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20142050.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20142057.png)

---

## Pre-Verification
### DSW1
```cisco
show etherchannel load-balance
show etherchannel port
show etherchannel summary
show etherchannel detail
show ip interface brief
show ip interface port-channel 1
```
![DSW1 preverification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20140719.png)
![DSW1 preverification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20140738.png)
![DSW1 preverification 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20140807.png)
![DSW1 preverification 4](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20140831.png)
![DSW1 preverification 5](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20140903.png)
![DSW1 preverification 6](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20140912.png)
![DSW1 preverification 7](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20141157.png)
![DSW1 preverification 8](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20141223.png)

### ASW1
![ASW1 preverification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20142835.png)

## Configuration Steps & Post Verification
### DSW1
```cisco
en
conf t
interface range f0/2 - 8
shutdown
channel-group 1 mode on
no shutdown
```
![DSW1 configuration](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20141945.png)

### ASW1
![ASW1 postverification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-31%20142852.png)
