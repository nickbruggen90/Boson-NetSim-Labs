## Objective
In this lab, you will configure Network Time Protocol (NTP) on several NTP client devices. You will additionally configure each of the client devices to authenticate NTP packets from the master NTP server. Also, you will use access control lists (ACLs) and NTP access groups to restrict NTP synchronization from the master NTP server and to the NTP clients.

Note: You should allow time for NTP polling interval expirations in several steps in this lab. In order to facilitate the speed at which the lab can be completed, NTP timers are faster in NetSim than what you would experience on live gear.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20135949.png)

![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20135955.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140003.png)
![connections chart 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140014.png)

---

## Configuration Steps
### Router1
```cisco
en
conf t
ntp authenticate
ntp authentication-key 1 md5 80$0n!
access-list 10 permit 203.0.113.2 0.0.0.0
ntp access-group serve-only 10
access-list 10 permit 203.0.113.6 0.0.0.0
```
![Router1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140025.png)

### CSW1
```cisco
en
conf t
ntp server 203.0.113.1
ntp authenticate
ntp authentication-key 1 md5 b0$0n
ntp trusted-key1
ntp server 203.0.113.1 key 1
no ntp authentication-key 1 md5 b0$0n
no ntp server 203.0.113.1 key 1
no ntp trusted-key 1
ntp authentication-key 1 md5 80$0n!
ntp trusted-key 1
ntp server 203.0.113.1 key 1
access-list 10 permit 203.0.113.1 0.0.0.0
ntp access-group peer 10
```
![CSW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140037.png)

### CSW2
```cisco
en
conf t
ntp server 203.0.113.5
ntp authenticate
ntp trusted-key 1
ntp authentication-key 1 md5 b0$0n
ntp server 203.0.113.5 key 1
no authentication-key 1 md5 b0$0n
no ntp server 203.0.113.5 key 1
no ntp trusted-key 1
ntp authentication-key 1 md5 80$0n!
ntp trusted-key 1
ntp server 203.0.113.5 key 1
access-list 10 permit 203.0.113.5 0.0.0.0
ntp access-group peer 10
```
![CSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140050.png)

### DSW1
```cisco
en
conf t
ntp server 203.0.113.9
access-list 10 permit 203.0.113.9 0.0.0.0
ntp access-group peer 10
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140057.png)

### DSW2
```cisco
en
conf t
ntp server 203.0.113.21
access-list 10 permit 203.0.113.21 0.0.0.0
ntp access-group peer 10
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140104.png)

### ASW1
```cisco
en
conf t
ntp server 203.0.113.9
access-list 10 permit 203.0.113.21 0.0.0.0
ntp access-group peer 10
```
![ASW1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140113.png)

### ASW2
```cisco
en
conf t
ntp server 203.0.113.22
access-list 10 permit 203.0.113.21 0.0.0.0
ntp access-group peer 10
```
![ASW2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140120.png)

---

## Verification
```cisco
show ntp associations
show ntp status
show access-lists
```
![verification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140236.png)
![verification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140248.png)
![verification 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140307.png)
![verification 4](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140320.png)
![verification 5](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140353.png)
![verification 6](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images2/Screenshot%202025-05-23%20140406.png)
