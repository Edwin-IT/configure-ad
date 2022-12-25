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

<h2>Overview</h2>

- Step 1:	Create a Domain Controller VM and a Client VM
- Step 2: Ensure Client-1 and DC-1 are connected
- Step 3: Install Active Directory
- Step 4: Create an Admin and Normal User Account in AD
- Step 5: Join Client-1 to domain
- Step 6: Setup Remote Desktop for non-administrative users on Client-1
- Step 7: Create additional users and log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://imgur.com/iTdCQLq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/5tPJbFU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/kMk8mEk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 1: Name Domain Controller VM “DC-1”, name Client VM “Client-1” use the same resource group and Vnet. Finally, set DC-1’s NIC Private IP address to be static.
</p>
<br />

<p>
<img src="https://imgur.com/bovasfi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/pYBMLwn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/b4tzWA9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 2: Initiate a perpetual ping from Client-1 to DC-1. For it to succeed, enable ICMPv4 in DC-1 in windows Firewall.
</p>
<br />

<p>
<img src="https://imgur.com/hEx9gqc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/9fVRwXg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/Ed5TSCp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 3: In DC-1 install Active Directory Domain Services. Promote as a DC, and name root domain name mydomain.com as a new forest. The DC VM should sign itself out.
</p>
<br />

<p>
<img src="https://imgur.com/jwZOv0W.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/gpKVVVV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 4: In Active Directory Users and Computers (ADUC), create an Organizational Unit called “_EMPLOYEES”, then create “_ADMINS”. Create a new employee and add Jane admin to admins, use jane_admin to log into DC-1.
</p>
<br />

<p>
<img src="https://imgur.com/iomjybe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/mmKXjen.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/aI8DNiB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 5: In Azure Portal, set Client-1’s DNS settings to DC-1’s Private IP address, then restart Client-1. Then log into Client-1 with labuser and join it to the domain. In the Domain Controller, Client-1 will be inside “Computers”.
</p>
<br />

<p>
<img src="https://imgur.com/vA30d4I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 6: Log into Client-1 as mydomain.com\jane_admin and open system properties, then click “Remote Desktop”, then allow “domain users” access to remote desktop.
</p>
<br />

<p>
<img src="https://imgur.com/4esqNKC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/8juaSTq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 7: Login to DC-1 as jane_admin, then, Open PowerShell_ise as an administrator. Paste random account script into it, run the script and the account will start creating. Finally log into Client-1 with one of the random accounts.
</p>
<br />
