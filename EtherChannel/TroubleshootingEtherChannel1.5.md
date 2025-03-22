# 🔧 Optimizing Network Utilization

## 🧠 Lab Purpose
System administrators have configured PC2 to operate as a file server handling requests from hosts that are connected to ASW1. 
While executing load stress testing scenarios, it is discovered that the server is unable to deliver the expected bandwidth to the hosts. 
Other network traffic appears to not be affected. You have been tasked with finding the reason that the server is unable to utilize 
the optimal network bandwidth and correcting the problem.
  
> In this lab we will optimize network traffic by applying the appropriate load balancing techniques.

---

## 🖥️ Topology Overview
![Topology Diagram](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-03-21%20160929.png)
> Devices involved in EtherChannel configuration: 
> - ASW1 ↔ DSW1 (EtherChannel bundle)
> - DSW1 ↔ ASW2 (EtherChannel bundle)
> - ASW2 ↔ PC2 (EtherChannel bundle)
> - ASW2 ↔ DSW2 (EtherChannel bundle)
> - ASW1 ↔ DSW2 (EtherChannel bundle)
---
## ⚙️ Configuration Steps

### 🔹 ASW2 Configuration
```cisco
en
show cdp neighbors
show etherchannel summary
show mac-address-table
show interfaces g0/1
conf t
port-channel load-balance src-dst-mac
exit
```
---
## ✅ Verification
### 🔹 PC2 Verification
```cisco
ipconfig /all
```
### 🔹 ASW2 Verification
```cisco
show mac-address-table
show interfaces g0/1
```
### 🔎Verification Output  
![show mac-address-table](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-03-21%20172103.png)
![PC2, ipconfig /all](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-03-21%20172224.png)
![show interfaces g0/1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-03-21%20172206.png)

---
### Troubleshooting Notes
* Cisco switches use PAgP by default  
* Non-Cisco switches typically support only LACP or static EtherChannel  
* PAgP is Cisco proprietary, this was the cause for links to *(I) Individual Mode*  
✅Fix: Use `mode active` to enable LACP for compatibility with non-Cisco switches  

---
### Key Takeaways
* Use LACP (active/passive) instead of PAgP when connecting non-Cisco switches  
* `mode auto` will not form an EtherChannel on non-Cisco switches  
* Always double check EtherChannel negotiation protocol compatibility in multi-vendor environments  

---
### Related Labs

