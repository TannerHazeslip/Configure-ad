# Configure-ad
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

<p>
  Create a resource group, a Virtual Network and Subnet in Microsoft Azure
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161407530929487913/Capture.PNG?ex=6538300d&is=6525bb0d&hm=35f39ede9344a72d88f800cb8bc48274fa3b0fec82daf3cdaf15fbec4172d87b&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161407766330622042/Capture.PNG?ex=65383045&is=6525bb45&hm=394f09060d24605ef5270a30495c48a04f57b009c767f81a62dd3bff7fcadd86&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Create a client resource group
 <img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161408854685392936/Capture.PNG?ex=65383148&is=6525bc48&hm=33f3723e0ccf4627d9108cd722e14f373799a096ed1e5262f9067167118e89de&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161409079273590904/Capture.PNG?ex=6538317e&is=6525bc7e&hm=795379639194400dfc80553acd311812d197cc089e7f60c75d7be0dec005ad0d&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161409440499634196/Capture.PNG?ex=653831d4&is=6525bcd4&hm=a1936e9514c5fbc0704c5b7aa9d32049b350be80ceee91d57989dd27a6dd3122&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Set the Domain Controllers NIC private OP address to static by going to virtual machines - DC-1(or whatever you named the resource group) - Networking - Network interface - IP configurations
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161410442728571023/Capture.PNG?ex=653832c3&is=6525bdc3&hm=52cae90ac16c2cb47e03b96904ae4d16462eb37f6b9984effacd0f64a3974759&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
</p>
Login to the Domain Controller and enable ICMPv4 on the local windows firewall
<br />
Open remote desktop and enter the IP of the VM
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161411389634642012/Capture.PNG?ex=653833a5&is=6525bea5&hm=9b71983bf1a9680dd28fb4cba4c433add445ab2ec7c3bdb032f61253bd299b53&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Open windows firewall inside the VM and enable both ICMP echo request rules
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161412710840401930/Capture.PNG?ex=653834e0&is=6525bfe0&hm=1bdae8dfa276a167ce234e5e1f2935293f06b3a5b2370298ca55466caf399096&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161412864767184937/Capture.PNG?ex=65383504&is=6525c004&hm=5d84f652c1bff0e74b1693f0a756b30ea3c8a17dc54f9c531d3007421912a034&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Install Active Directory Donain Services on the domain controller
<p>
Go to server manager(it should be open by default on the VM but it can be opened from the windows search function as well) and click on add roles and features
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161414047078547527/Capture.PNG?ex=6538361e&is=6525c11e&hm=4d0869a08828f7d90c4ffac2b99caf2d003f5e8b548ea4902576203189617c03&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Click next until you get to server roles and make sure you select Active Directory Domain Services
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161414463275151410/Capture.PNG?ex=65383682&is=6525c182&hm=73b4e050a5fca112aa6d3ebd3d0bcd323180c0c59b52c274a70cda1931058a8a&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Click next until you get to the confirmation and then click install
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161414911977586749/Capture.PNG?ex=653836ed&is=6525c1ed&hm=0b76309dea35164c5a821f56beacf338abf6b70ca3ffd371adca03137c623e5e&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Promote the server to a domain controller
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161415386969936023/Capture.PNG?ex=6538375e&is=6525c25e&hm=b42038bab0fe388cc4eefe4e7c59460571fa93adc5ebfb1b77d57eb28f394f2e&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
