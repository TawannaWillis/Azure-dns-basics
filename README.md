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
<img src="https://i.imgur.com/2dervb7.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/OS2G5ro.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/dlI13Rk.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/cJbZ65Z.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
<br />-Log into DC-1 and Client-1 as tawannatest\jane_admin.
<br />-On Client-1: Ping "mainframe" (it fails). Then Run nslookup mainframe (no DNS record).
<br />-On DC-1: Create a DNS A-record for "mainframe" pointing to DC-1’s private IP.
<br />-On Client-1: Ping "mainframe" again (it works).




</p>
<br />

<p>
<img src="https://i.imgur.com/4fY6Oct.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/fvv3o3K.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/b2t2A7V.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/b1vIyMb.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
<br />-On DC-1, update "mainframe" record address to 8.8.8.8.
<br />-On Client-1:Ping "mainframe" (still pings old address).
<br />-Check local DNS cache: ipconfig /displaydns.
<br />-Flush cache: ipconfig /flushdns.
<br />-Verify cache is empty: ipconfig /displaydns.
<br />-Ping "mainframe" again (new address shows up).


</p>
<br />

<p>
<img src="https://i.imgur.com/rI2NYU7.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/FmVM0IU.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/dyWduSW.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/22HXGfI.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
On DC-1: Create a CNAME record pointing "search" to www.google.com.
On Client-1: Ping "search" and observe the CNAME results. Run nslookup search and observe the results.
</p>
<br />

<h2>Lessons Learned </h2>

This lab made me understand how DNS directly works on a computer and the network. DNS records can change and sometimes this can cause connectivity issues. The DNS cache may have the old records and needs to be cleared out to update to the new records. The ipconfig /flushdns command is a common troubleshooting tool that has been referenced a lot in IT programs and I did not get a complete understanding how and why this works until I have done this lab. In the context of pinging "mainframe" at the start of the lab, the DNS cache gets checked first. If there is no result, the host file will be checked. The DNS server will be checked if there are no results in the host file. I made a record on the DNS server so a ping to mainframe can resolve. A CNAME record maps an alias name to another domain name. In this case, "search" was another name for Google
