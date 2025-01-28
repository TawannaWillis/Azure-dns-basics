<p align="center">
<img src="https://i.imgur.com/3OaAdju.png" alt="DNS Photo"/>
</p>

<h1>Understanding DNS</h1>


This lab focuses on understanding and managing Domain Name System (DNS) records within an Active Directory environment. The exercises simulate real-world scenarios to enhance skills in DNS configuration, troubleshooting, and optimization. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Command Prompt

 <h2>Skills</h2>

- DNS Configuration and Management
- Troubleshooting DNS Issues
- Using Networking Tools (ping, nslookup, ipconfig)
  
<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>DNS Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/5pjgtVz.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/Zl04Jyt.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/96xUgLF.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
<br />-Log into DC-1 and Client-1 as tawannatest\jane_admin.
<br />-On Client-1: Ping "mainframe" (it fails). Then Run nslookup mainframe (no DNS record).
<br />-On DC-1: Create a DNS A-record for "mainframe" pointing to DC-1’s private IP.
<br />-On Client-1: Ping "mainframe" again (it works).




</p>
<br />

<p>
<img src="https://i.imgur.com/nLlOGKl.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/p0VcajB.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/ds0SCKW.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/d4cXTCS.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
This next exercise will showcase the DNS cache. On the domain controller, I changed mainframe's record address to 8.8.8.8 (Google) and refreshed the DNS server. When pinging mainframe on the client, it will still ping the old IP address. When the command ipconfig /displaydns is run, it will reveal that the DNS cache still has the old IP. In order to update the cache, we need to clear it. The command ipconfig /flushdns will empty the cache so that when we ping mainframe again, the IP address will be updated to the new one on the client side. When pinging mainframe, the new IP address of the record will show.
</p>
<br />

<p>
<img src="https://i.imgur.com/rI2NYU7.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/FmVM0IU.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/dyWduSW.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
A CNAME record will now be made on the DNS server that will point "search" to Google. On the Forward Lookup Zones tab in the DNS Manager, open the tab that has the domain. Create a new CNAME record called search and point it to Google. Refresh the server to save the changes. On the client, pinging search and using nslookup will return the results of the CNAME record.
</p>
<br />

<h2>Lessons Learned </h2>

This lab made me understand how DNS directly works on a computer and the network. DNS records can change and sometimes this can cause connectivity issues. The DNS cache may have the old records and needs to be cleared out to update to the new records. The ipconfig /flushdns command is a common troubleshooting tool that has been referenced a lot in IT programs and I did not get a complete understanding how and why this works until I have done this lab. In the context of pinging "mainframe" at the start of the lab, the DNS cache gets checked first. If there is no result, the host file will be checked. The DNS server will be checked if there are no results in the host file. I made a record on the DNS server so a ping to mainframe can resolve. A CNAME record maps an alias name to another domain name. In this case, "search" was another name for Google
