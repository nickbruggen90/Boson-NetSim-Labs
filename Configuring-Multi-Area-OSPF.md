## Objective
Configure Open Shortest Path First (OSPF) for proper operation in a multi-area environment. Configure route summarization to reduce the size of the routing tables and the OSPF link-state database.

---

## Lab Topology
The lab topology displays information about the network devices in the lab.
![topology](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20082918.png)
![connections table](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20082944.png)

---

## Configuration Steps
### P1R1
```cisco
en
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 1
network 10.100.100.0 0.0.0.255 area 0
area 1 range 192.168.1.0 255.255.255.192
```
![P1R1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083410.png)

### P1R2
```cisco
en
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 1
```
![P1R2 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083417.png)

### P1R3
```cisco
en
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 1
```
![P1R3 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083426.png)

### P2R1
```cisco
en
conf t
router ospf 2
network 192.168.2.0 0.0.0.255 area 2
network 10.100.100.0 0.0.0.255 area 0
area 2 range 192.168.2.0 255.255.255.192
```
![P2R1 commands](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083437.png)

---

## Verification
```cisco
show ip ospf
show ip route
show ip route ospf
show ip ospf database
show ip ospf neighbor
```
![show ip ospf 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083507.png)
![show ip ospf 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083513.png)
![show ip route](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083526.png)
![show ip route ospf](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083540.png)
![show ip ospf database](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083557.png)
![show ip ospf neighbor](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-19%20083618.png)
![P2R1 1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20071838.png)
![P2R1 2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20071851.png)
![P2R1 3](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20071921.png)
![P2R1 4](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20071934.png)
![P2R1 5](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20071948.png)
![P2R1 6](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-22%20072000.png)

