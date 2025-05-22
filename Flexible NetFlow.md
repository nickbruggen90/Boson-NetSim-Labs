## Objective  
In this lab, you will learn the basic commands to configure Flexible NetFlow on a Cisco router and to verify an existing Flexible NetFlow configuration.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20051416.png)

---

## Configuration Steps

### Router1
```cisco
en
conf t
flow exporter EXPORTER1
destination 10.1.1.100
source loopback 0
transport udp 2055
exit
flow record LANFLOW1
match interface input
match ipv4 destination address
match ipv4 source address
match ipv4 protocol
match ipv4 tos
match transport destination-port
match transport source-port
collect counter bytes
collect counter packets
collect interface output
collect routing next-hop address ipv4
collect timestamp sys-uptime first
collect timestamp sys-uptime last
exit
flow monitor MONITOR1
description Primary NetFlow Cache
record LANFLOW1
exporter EXPORTER1
exit
interface f0/0
ip flow monitor MONITOR1 input
```
![router1_commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20052138.png)

---

## Verification

```cisco
en
show flow monitor
```
![router1_verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-14%20052219.png)

---

