## Objective
Configure the router named Regional to work with the local database, and enable a password and line authentication in order to provide Authentication, Authorization, and Accounting (AAA) services. In the first task of this lab, you will use AAA to authenticate against the local database for the enable, line, and local methods. In the second task, you will configure exec authorization against the local user database. In the third task, you will configure the HQ router to authenticate against the Cisco Secure Access Control System (ACS) database.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. For this lab, your network design includes two routers, HQ and Regional, which are connected by a serial link. Workstation, a PC, is connected to a Fast Ethernet port on HQ, and a Terminal Access Controller Access Control System Plus (TACACS+) server is connected to a Fast Ethernet port on Regional. Upon the initial loading of the lab, all devices will be configured with the IP addresses and routing protocols needed for connectivity.
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20074657.png)

---

## Configuration Steps
### Regional
```cisco
en
conf t
aaa new-model
username regionaluser password regionalpass
enable password training
aaa authentication login default enable
aaa authentication login local_authent local
line vty 0 4
login authentication local_authent
exit
username regionaladmin privilege 15 password adminpass
aaa authorization exec local_author local
line vty 0 4
authorization exec local_author
```
![regional commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20075014.png)

### HQ
```cisco
en
conf t
tacacs host 192.168.2.254
tacacs key boson
aaa authentication login aaa_login group tacacs+ local
aaa authorization exec aaa_exec group tacacs+ local
line vty 0 4
authorization exec aaa_exec
login authentication aaa_login
exit
aaa authentication enable default group tacacs+ enable
```
![hq commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20075301.png)

