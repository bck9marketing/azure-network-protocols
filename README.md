<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we will observe various network traffic to and from Azure Virtual Machines with Wireshark as well as briefly experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Install a Windows 10 VM and an Ubuntu VM within the same Resource Group and Virtual Network
- Install Wireshark
- Experiment with Network Security Groups
- Observe various types of network traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/b6cd9460-ecbf-4754-95e2-9de8ffbb095b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/506a63dd-3645-41a6-9605-ce38da4e5b57" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/b7dbce68-15a5-4b1b-b2b3-55a265d31652" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/d5c5f535-9efb-4e29-a648-d8a27a196dcc" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We're going to start off with creating 2 virtual machines within the same Resource Group and Virtual Network. I have some tutorials in my other repositories if you don't already know how to do this. Look to the pictures above to see the settings I used. The first VM will be Windows 10 pro, and our image size for both VMs will be 2vcpu w/ 16GiB of memory. Our second VM will be running Ubuntu Server 20.04. Let your first VM deploy before creating VM2. When starting the creation of VM-2, make sure to refresh your page first so that your previously created Virtual Network populates correctly. As always for these tutorials we will use user:testaccount \ password: Testpassword1 .
</p>
<br />

<p>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/900388bc-cdec-4963-b81c-c06b7f35a6d4" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log in to VM-1/Windows10 and download/install Wireshark, this will allow us to monitor our network traffic. 
</p>
<br />

<p>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/908549a9-c2cb-4442-ba62-5b79e4cfd681" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/b3585ce2-eb42-445e-8297-d8cc4d8413bc" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open up Wireshark and click the blue shark in the top left to get start monitoring network traffic. From here, type in "icmp" and hit enter.
</p>
<br />

<p>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/438639e3-596b-47e1-8efa-738f241cce1a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/e0ba77ef-790b-4c8d-bcb5-2b9e5917e29e" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Since we are filtering by the "Internet Control Message Protocol"(ICMP), our filtered results will be empty at this point. To see Wireshark's network filtering in action, grab your Ubuntu VM's(VM-2) private IP and ping it from within VM-1. You should now be able to see this network traffic through Wireshark.
</p>
<br />

<p>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/0a32d509-a1ea-43b6-b0bb-823a532dccc6" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/5ae26312-158d-4220-a003-d3b55e0bdd10" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/bck9marketing/azure-network-protocols/assets/159003800/5a69fe08-dcd1-415b-bd9e-6ebd05513e28" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We can now play around with Network Security Groups by heading back to your VM-2's Overview page and going to the Networking tab. Here we will add an "Inbound Security Rule" denying ICMP from any source. Click "Add inbound port rule", Select "ICMP" under protocol, "Deny" under "Action", type in "200" for "Priority", and name it "DENY_ICMP_PING_FROM_ANYWHERE". Click "Add". Now when we refresh our page, we should see our new rule listed. The first picture shows how you can do this from VM-2's Overview page but the third picture shows the dedicated "Network Security Groups" page. From here you would just click on VM-2 and then "Inbound security rules". 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />


