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
<img src="https://i.imgur.com/0IMEo4o.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/kLw5lp2.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/sgGCvB3.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
<br />-On DC-1: Create a CNAME record pointing "search" to www.google.com.
<br />-On Client-1: Ping "search" and observe the CNAME results. Run nslookup search and observe the results.
</p>
<br />

<h2>Lessons Learned </h2>

Through this lab, I learned how to create and verify A-records to map hostnames to IP addresses, ensuring proper communication between devices. I also gained an understanding of local DNS caching and how to observe and clear cached records to force DNS updates. Additionally, I practiced creating CNAME records to alias hostnames, which can streamline hostname resolution. The lab also enhanced my troubleshooting skills, using tools like `ping` and `nslookup` to diagnose and resolve DNS-related issues. Overall, this exercise provided valuable hands-on experience in managing and troubleshooting DNS records.
