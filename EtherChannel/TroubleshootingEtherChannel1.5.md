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

## ⚙️ Configuration Steps

### 🔹 ASW2 Configuration
```cisco
en
show cdp neighbors
show etherchannel summary
show mac-address-table
show ip interfaces g0/1
conf t
port-channel load-balance src-dst-mac
exit
```

### 🔹 PC2 Verification
```cisco
ipconfig /all
```
