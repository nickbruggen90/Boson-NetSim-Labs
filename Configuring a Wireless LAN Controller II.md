## Objective
Explore the steps required to configure different security models on a Cisco 9800 Wireless LAN Controller (WLC). Configure the Campus location’s wireless local area network (WLAN) to use 802.1x Extensible Authentication Protocol (EAP) with Remote Authentication Dial-In User Service (RADIUS) authentication. Create a guest WLAN and configure it to authenticate by using Web Authentication (WebAuth).

For this lab, your network design will include a Catalyst 3550 switch named WSW, a WLC named WLC, a lightweight access point (AP) named AP, an Identity Services Engine (ISE) server named ISE, and a PC named PC-Admin. WLC, AP, ISE, and PC-Admin are each connected to WSW via FastEthernet ports. This lab will not involve configuring any devices but instead will guide you through the steps of configuring the WLC and ISE by using screenshots from real-world hardware.

---
![1](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160005.png)
![2](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160023.png)
![3](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160106.png)
![4](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160121.png)
![5](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160131.png)
![6](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160146.png)
![7](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160200.png)
![8](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160215.png)
![9](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160227.png)
![10](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160238.png)
![11](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160254.png)
![12](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160306.png)
![13](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160317.png)
![14](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160328.png)
![15](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160340.png)
![16](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160351.png)
![17](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160402.png)
![18](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160414.png)
![19](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160425.png)
![20](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160439.png)
![21](https://github.com/nickbruggen90/Boson-Network-Labs/blob/main/Images/Screenshot%202025-05-21%20160446.png)

