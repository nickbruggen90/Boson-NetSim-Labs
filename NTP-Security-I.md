## Objective
In this lab, you will configure Network Time Protocol (NTP) on a master NTP server and on two NTP client devices. You will additionally configure each of the client devices to authenticate NTP packets from the master NTP server. Also, you will use access control lists (ACLs) and NTP access groups to restrict NTP synchronization from the master NTP server and to the NTP clients.

Note: You should allow time for NTP polling interval expirations in several steps in this lab. In order to facilitate the speed at which the lab can be completed, NTP timers are faster in NetSim than what you would experience on live gear.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123452.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123509.png)
![connecyions chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123514.png)

---

## Configuration Steps
### Router1
```cisco
en
clock set 18:09:00 26 Aug 2014
conf t
ntp master 10
ntp authenticate
ntp authentication-key 1 md5 boson
access-list 10 permit 192.168.51.49
ntp access-group serve-only 10
```
![Router1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123523.png)

### DSW1
```cisco
en
show clock
conf t
ntp authenticate
ntp authentication-key 1 md5 boson
ntp trusted-key 1
ntp server 192.168.51.49 key 1
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123532.png)

### DSW2
```cisco
en
show clock
conf t
ntp authenticate
ntp authentication-key 1 md5 bo$on
ntp trusted-key 1
ntp server 192.168.51.49 key 1
np ntp authentication-key 1 md5 bo$on
ntp authentication-key 1 md5 boson
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123542.png)

---

## Verification
```cisco
show ntp associations
show ntp status
show clock
```
![verification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123605.png)
![verification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123620.png)
![verification 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123634.png)
![verification 4](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123714.png)
![verification 5](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123719.png)
![verification 6](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20123726.png)
