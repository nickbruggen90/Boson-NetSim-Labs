# 🔧 Optimizing Network Utilization

## 🧠 Lab Purpose
System administrators have configured PC2 to operate as a file server handling requests from hosts that are connected to ASW1. 
While executing load stress testing scenarios, it is discovered that the server is unable to deliver the expected bandwidth to the hosts. 
Other network traffic appears to not be affected. You have been tasked with finding the reason that the server is unable to utilize 
the optimal network bandwidth and correcting the problem.
  
> In this lab we will optimize network traffic by applying the appropriate load balancing techniques

---

## 🖥️ Topology Overview
![Topology Diagram](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-03-21%20160929.png)
> Devices involved in EtherChannel configuration: 
> - DSW1 ↔ CSW1 (EtherChannel bundle)
> - DSW2 ↔ CSW1 (EtherChannel bundle)
> - DSW1 ↔ CSW2 (EtherChannel bundle)
> - DSW2 ↔ CSW2 (EtherChannel bundle)

**CSW1 is the non-Cisco temporary replacement switch**
