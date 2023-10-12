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
Go to the server manager and click on add roles and features
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161414047078547527/Capture.PNG?ex=6538361e&is=6525c11e&hm=4d0869a08828f7d90c4ffac2b99caf2d003f5e8b548ea4902576203189617c03&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Click next until you get to server roles and select Active Directory Domain Services
<p>
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161414463275151410/Capture.PNG?ex=65383682&is=6525c182&hm=73b4e050a5fca112aa6d3ebd3d0bcd323180c0c59b52c274a70cda1931058a8a&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Click next until you get to this screen and click install
  
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161414911977586749/Capture.PNG?ex=653836ed&is=6525c1ed&hm=0b76309dea35164c5a821f56beacf338abf6b70ca3ffd371adca03137c623e5e&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Promote the server to a domain controller
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1161415386969936023/Capture.PNG?ex=6538375e&is=6525c25e&hm=b42038bab0fe388cc4eefe4e7c59460571fa93adc5ebfb1b77d57eb28f394f2e&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Name the domain controller and create a password
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162115888611340298/Capture.PNG?ex=653ac3c2&is=65284ec2&hm=200593515b55c5a6a59608c142d7a9ccca57b16ea1450e9422567cd1a71e823c&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162116425314472047/Capture.PNG?ex=653ac442&is=65284f42&hm=64289bb22a0f1e4882f3f35294d6639e242ad293131f901ce65a5c004f5673a9&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Hit next until you get to this screen and then hit install to set up active directory(this will shut down the remote desktop connection so a reconnect is required)
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162116968602685470/Capture.PNG?ex=653ac4c4&is=65284fc4&hm=b61a1235b7a52cd59c13172fc72c00c31e80312680ae6cb5eb6077f4c1d203c6&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Open active directory in the VM and create organizational units
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162118542716571678/Capture.PNG?ex=653ac63b&is=6528513b&hm=f519d016603b4a7234dd2ea5c69a7a414c4cb1050c854341c93cad0975d90a7f&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162118761520840896/Capture.PNG?ex=653ac66f&is=6528516f&hm=31f11d376c45e6c168d033cac43d5bdc95477cde38a0223d7b8bdf6c1ed21f31&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162118995873378404/Capture.PNG?ex=653ac6a7&is=652851a7&hm=44296fd0b7ac3f298adf83642afd7195be01dba90d0736ba056fdfcb113b317c&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
</p>
Create a new user in the admin organization group
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162121773505061037/Capture.PNG?ex=653ac93d&is=6528543d&hm=9745e3ab7c795e270137aad67c56b6407a1015cb5f0b420036b979be03a931f3&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
Create a password for the user and check any of the boxes that apply
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162122431851417771/Capture.PNG?ex=653ac9da&is=652854da&hm=2e003fbd11fe4cae8f8723da07a2a35585d856a7c173807a62cd40c63109671f&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
Assign this user to the domain admin group
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162122834043228332/Capture.PNG?ex=653aca3a&is=6528553a&hm=920987d1175e506fa1529953c690986df2801339baf07ff2e5a763a44ca8ea4e&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162122958156877844/Capture.PNG?ex=653aca58&is=65285558&hm=77bdb668c9f1b173477ef384b83143b51ffb61d9cfd1571b928c2df486e8fdc5&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
Type in "domain admins" and click check names
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162123763173838942/Capture.PNG?ex=653acb18&is=65285618&hm=abb1690aaabc89005697295cdc5115d99023f680f44fe02cbc077c707e8b8974&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162123136280559727/Capture.PNG?ex=653aca82&is=65285582&hm=e2fc7add2be9642f058e2ad750e91d9055f632c3d2a61b17eaa43174da9a905b&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1149514851564138576/1162124060331872377/Capture.PNG?ex=653acb5f&is=6528565f&hm=60174cb31ac627b191054b9d71f68242df8088aac3e580a8bfda673474de0789&" height="40%" width="60%" alt="Disk Sanitization Steps"/>
<p>
Log out of the domain controller and log back in as the admin you created
</p>
<br />
