## Objective
Configure P1R1 for basic external Border Gateway Protocol (eBGP). Configure P1R1 and P1R2 for internal Border Gateway Protocol (iBGP). Confirm Border Gateway Protocol (BGP) connectivity.

Configure P1R1 and P1R2; P1R3 will not be configured in this lab. Pod 2 has already been configured upon the initial loading of the lab.

---

## Lab Topology
The topology diagram below represents the NetMap in the Simulator.
![topology](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20104810.png)
![connections chart 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20104815.png)
![connections chart 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20104820.png)

---

## Configuration Steps
### P1R1
```cisco
en
conf t
hostname P1R1
interface loopback 0
ip address 192.168.1.1 255.255.255.240
interface f0/0
ip address 10.100.100.1 255.255.255.0
no shutdown
interface serial 0/0
ip address 192.168.1.33 255.255.255.240
clock rate 64000
exit
router bgp 1
neighbor 10.100.100.2 remote-as 2
neighbor 192.168.1.34 remote-as 1
network 192.168.1.0 mask 255.255.255.240
network 192.168.1.32 mask 255.255.255.240
network 10.100.100.0 mask 255.255.255.0
```
![P1R1 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20104832.png)

### P1R2
```cisco
en
conf t
hostname P1R2
interface loopback 0
ip address 192.168.1.17 255.255.255.240
interface f0/0
ip address 192.168.1.49 255.255.255.240
no shutdown
interface serial 0/0
ip address 192.168.1.34 255.255.255.240
exit
router bgp 1
neighbor 192.168.1.33 remote-as 1
network 192.168.1.16 mask 255.255.255.240
network 192.168.1.32 mask 255.255.255.240
network 192.168.1.48 mask 255.255.255.240
```
![P1R2 commands](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20104845.png)

---

## Verification
```cisco
show ip route bgp
show ip route
show ip protocols
show bgp neighbors
show ip bgp
```
![verification 1](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20105117.png)
![verification 2](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20105142.png)
![verification 3](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20105152.png)
![verification 4](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20105204.png)
![verification 5](https://github.com/nickbruggen90/Boson-NetSim-Labs/blob/main/Images3/Screenshot%202025-05-28%20105215.png)
