# 🔧 Solving Bandwidth Issues After Switch Replacement

## 🧠 Lab Purpose
Due to hardware failure, **CSW1** has been temporarily replaced with a **non-Cisco switch** until a satisfactory replacement 
can be delivered. Upon installation and configuration of the temporary switch, there is a **noticeable decrease of network 
bandwidth** between the core and distribution layers. You are provided authorization to the **access and distribution 
switches**, and you have been asked to determine and correct the problem.

> Example:  
> In this lab we will verify EtherChannel set-up and modify configurations to allow for a mult-vendor environment

---

## 🖥️ Topology Overview

> Devices involved in EtherChannel configuration: 
> - DSW1 ↔ CSW1 (EtherChannel bundle)
> - DSW2 ↔ CSW1 (EtherChannel bundle)
> - DSW1 ↔ CSW2 (EtherChannel bundle)
> - DSW2 ↔ CSW2 (EtherChannel bundle)

###**CSW1 is the non-Cisco temporary replacement switch**

## ⚙️ Configuration Steps

### 🔹 DSW1 Verification and Configuration
en
show cdp neighbors
show etherchannel summary
show running-configuration
conf t
interface range f0/9 - 10
no channel-group 11 mode auto
channel-group 11 mode active

### 🔹 DSW2 Verification and Configuration
en
show cdp neighbors
show etherchannel summary
show running-configuration
conf t
interface range f0/7 - 8
no channel-group 21 mode auto
channel-group 21 mode active

### Troubleshooting Notes
Cisco switches use PAgP by default
Non-Cisco switches typically support only LACP or static EtherChannel
PAgP is Cisco proprietary, this was the cause for links to (I) Individual Mode
Fix: use mode active to enable LACP for compatibility with non-Cisco switches

### Key Takeaways
Use LACP (active/passive) instead of PAgP when connecting non-Cisco switches
mode auto will not form an EtherChannel on non-Cisco switches
Always double check EtherChannel negotiation protocol compatibility in multi-vendor environments

### Related Labs
