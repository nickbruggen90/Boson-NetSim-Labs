## Objective
Learn how to configure and verify basic network device management using a Management virtual LAN (VLAN), Simple Network Management Protocol (SNMP), and Terminal Access Controller Access Control System (TACACS) authentication with local authentication as backup.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20090949.png)
![connections table](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20091001.png)

---

## Configuration Steps
### Router1
```cisco
en
conf t
interface f1/0.99
encapsulation dot1q 99
ip address 10.99.0.1 255.255.255.0
exit
snmp-server community Boson ro
snmp-server contact snmp@boson.com
snmp-server location R1_SNMP
snmp-server host 10.10.0.2 snmp_logs
conf t
aaa new-model
tacacs host 10.1.0.3
tacacs key boson
aaa authentication login aaa_authentication group tacacs+ local
aaa authorization exec aaa_author group tacacs+ local
username admin privilege 15 password boson
line vty 0 4
authorization exec aaa_author
login authentication aaa_authentication
```
![router1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20091012.png)

### Switch1
```cisco
en
conf t
vlan 99
name Management
interface vlan 99
ip address 10.99.0.2. 255.255.255.0
exit
ip default-gateway 10.99.0.1
snmp-server community Boson ro
snmp-server location S1_SNMP
snmp-server contact snmp@boson.com
snmp-server host 10.10.0.2 snmp_logs
aaa new-model
tacacs host 10.1.0.3
tacacs key boson
aaa authentication login aaa_authentication group tacacs+ local
aaa authorization exec aaa_author group tacacs+ local
username admin privilege 15 password boson
line vty 0 15
login authentication aaa_authentication
authorization exec aaa_author
```
![switch1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20091022.png)

### Switch2
```cisco
en
conf t
interface vlan 99
ip address 10.99.0.3 255.255.255.0
exit
ip default-gateway 10.99.0.1
snmp-server community Boson ro
snmp-server location S1_SNMP
snmp-server contact snmp@boson.com
snmp-server host 10.10.0.2 snmp_logs
aaa new-model
tacacs host 10.1.0.3
tacacs key boson
aaa authentication login aaa_authentication group tacacs+ local
aaa authorization exec aaa_author group tacacs+ local
username admin privilege 15 password boson
line vty 0 15
login authentication aaa_authentication
authorization exec aaa_author
```
![switch2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20091032.png)

---

## Verification
```cisco
show snmp community
show snmp contact
show snmp host
show snmp location
```
![verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20091126.png)
