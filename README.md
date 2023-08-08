# ⚠️ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting⚠️

This project is a sub-project to my [ESXi-Home-SOC-Lab-Network-Overview](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Network-Overview).

Here I demonstrate some basic troubleshooting when I encountered a problem accessing the internet with web browsers on a mock workstation machine. 
Below is the layout of the network being used:

![V2-01222021-CYBER-INTERFACE-HD](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/ff8d0292-d86a-4f4f-b2bb-18cd34bf370c)


Workstation PELICAN 1 is not able to use the web browser to access web sites:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/a8a115ae-6865-4226-9e41-02bc3fc4c12f)

Though it is able to ping external IPs:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/e747f3e6-4b20-45a3-8135-6a0dd634e197)

Even though I have the evidence that it works, I wanted to double check the router configuration if there was anything strange preventing me from getting access to web pages.  

I verified the NAT settings in the GE0/0 interface:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/bf9889b8-625c-436c-8a94-f6355a1cffb8)

**NOTE** In this instance, PELICAN 2 is currently set with an IP of 192.168.0.6, **NOT** 192.168.10.6 shown in the map.

I tested and confirmed that PELICAN 2 is able to access the internet using web browser:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/3aefbf7d-434d-475d-aaf9-1f2e397d7ad7)
![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/58501a09-9236-4a93-ab76-687340c962ff)

Knowing it has full internet access, I looked at PELICAN 2's network configuration settings:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/f2899876-407e-4af2-b0c1-587019440067)

I compared it to PELICAN 1's network configuration, and noticed PELICAN 1 did not have a DNS server set up:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/6e7b3c5d-ba53-43ea-834b-7c63b35641f9)

Upon entering a DNS server (The Router's interface IP with the 192.168.10.0/24 network), I was able to successfully get to a web page in PELICAN 1 now:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/31488741-61d5-4696-be0b-95da1268d330)

Important to note that even with the globe icon in the bottom right, it is still connected to the ARK.local domain:

![image](https://github.com/gervguerrero/ESXi-Home-SOC-Lab-Basic-Internet-Troubleshooting/assets/140366635/79c58d3e-a854-4ff6-903b-10092e9e9501)

So the issue was that while I had my router configuration correct, I didn't set a DNS server for PELICAN 1. I was able to ping external websites by IP, but I was not able to resolve domain names to IPs in my web browser since no DNS server was set.
