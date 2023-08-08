# ⚠️ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting⚠️

This project is a sub-project to my [ESXi-Home-SOC-Lab-Network-Overview](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Network-Overview).

Here I demonstrate some basic troubleshooting when I encountered a problem accessing the internet with weh browsers on a mock workstation machine. 
Below is the layout of the network being used:
![V2-01222021-CYBER-INTERFACE-HD](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/ff8d0292-d86a-4f4f-b2bb-18cd34bf370c)


Workstation PELICAN 1 is not able to use the web browser to access web sites:
![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/a8a115ae-6865-4226-9e41-02bc3fc4c12f)

Though it is able to ping external IPs:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/e747f3e6-4b20-45a3-8135-6a0dd634e197)

Even though I have the evidence that it works, I wanted to double check the router configuration if there was anything strange from preventing me from getting access to web pages.  

I verified the NAT settings in the GE0/0 interface:
![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/bf9889b8-625c-436c-8a94-f6355a1cffb8)

**NOTE** In this instance, PELICAN 2 is currently set with an IP of 192.168.0.6, **NOT** 192.168.10.6 shown in the map.

I tested and confirmed that PELICAN 2 is able to access the internet using web browser:

