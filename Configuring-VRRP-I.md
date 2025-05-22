## Objective
Configure Virtual Router Redundancy Protocol (VRRP), and verify the configuration.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator. For this lab, your network design includes four switches: ASW1, ASW2, DSW1, and DSW2. The switches are connected to one another by Ethernet links. ASW1 and ASW2 are access layer switches, and DSW1 and DSW2 are distribution layer switches. Two workstations, named Client1 and Client2, are connected to the access layer switches on FastEthernet port 0/3.
![topology pic](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114019.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114054.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114110.png)

---

## Configuration Steps
### DSW1
```cisco
en
conf t
interface vlan 1
vrrp 3 ip 172.16.3.1
vrrp 3 priority 90
```
![DSW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114412.png)

### DSW2
```cisco
en
conf t
interface vlan 1
vrrp 3 ip 172.16.3.1
vrrp 3 priority 120
```
![DSW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114424.png)

### ASW1
```cisco
en
conf t
ip default-gateway 172.16.3.1
```
![ASW1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114433.png)

### ASW2
```cisco
en
conf t
ip default-gateway 172.16.3.1
```
![ASW2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114443.png)

### Client(s)
```cisco
ipconfig /dg 172.16.3.1
```
![clients](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20114450.png)

---

## Verification
```cisco
show vrrp
```
![DSW1 verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20115306.png)
![DSW2 verification](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20115328.png)
