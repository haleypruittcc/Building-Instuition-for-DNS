<p align="center">
<img src="https://wiki.hornbill.com/images/d/d6/Activedirectory_logo.png"/>
</p>

<h1>Active Directory</h1>
Active Directory is a software bulit and maintained by Microsoft that centrally manage thousands of user accounts in a single place, allows you to manage devices on a large scale, and provieds a way to control access to resource on a large scale. This tutorial we're going to be learning how to deploying active directtory and creating useres.
<h2>Tools and Requirements used </h2>

- Computer with Internet Connection
- Microsoft Azure
- Vitural Machines (Window Server 2022 and Windows 10)
- Remote Desktop
- Active Directory
<h2> Building Intuition for DNS </h2>


<h3>Step 1: A-Record Exercise </h3>


<p align="center">
<img src="https://i.imgur.com/PpaJXaF.png" height="80%" width="80%" alt="Azure Free Account"/>
  
 <p align="center">
<img src="https://i.imgur.com/miMxB2H.png" height="80%" width="80%" alt="Azure Free Account"/>

<p align="center">
<img src="https://i.imgur.com/l0Y5qiJ.png" height="80%" width="80%" alt="Azure Free Account"/>

- Connect/log into DC-1 as your domain admin account you create eariler (mydomain.com\haley_admin) 
- Connect/log into CLient-1 as a admin (mydomain\haley_admin).
- From Client-1 try ping "mainframe" notice that it fails.
- Nslookup "mainframe" notice that it fails (no DNS record)
- Create a DNS A- record on DC-1 for "mainframe" and have it point to DC-1's Private IP address
   - Service Manager -> DNS by Tools -> Forward -> on mydomain.com right click -> Lookup New Host -> mainframe and IP address.
     
- Go back to Clinet-1 and try to ping it. Observe that it works.


<h3>Step 2: Local DNS Cache Exercise  </h3>

<p align="center">
<img src="https://i.imgur.com/bVwhw0A.png" height="70%" width="70%" alt="Azure Free Account"/> 
</p>

<p align="center">
<img src="https://i.imgur.com/oJd7QDs.png" height="70%" width="70%" alt="Azure Free Account"/> 
</p>

<p align="center">
<img src="https://i.imgur.com/ke4FgYn.png" height="70%" width="70%" alt="Azure Free Account"/> 
</p>

<p align="center">
<img src="https://i.imgur.com/3uxWP0o.png" height="70%" width="70%" alt="Azure Free Account"/> 
</p>

- Go back to DC-1 and change mainframe's record address to 8.8.8.8
- Go back to Client -1 and ping "mainframe" again. 
   - Observe that it still ping the old address.
   - Type and observe the local dns cache (ipconfig/displaydns).
- Flush the DNS cache (ipconfig/flushdns).
   - Observe that the cache is empty.
- Attempt to ping "mainframe" again.
   - Observe the address of the new record is showing up.

<h3>Step 3:CNAME Record Exercrise  </h3>

<p align="center">
<img src="https://i.imgur.com/NZphUuj.png" height="70%" width="70%" alt="Azure Free Account"/> <img src="https://i.imgur.com/khVaiOJ.png" height="70%" width="70%" alt="Azure Free Services"/>
</p>

<p align="center">
<img src="https://i.imgur.com/88YbXLG.png" height="70%" width="70%" alt="Azure Free Account"/> 
</p>

- Go back to DC-1 and create a CNAME record that points the host "search" to "www.google.com".
- Go back to Client-1 and attempt to ping "search"
    - Observe the results of the CNAME record.
    - On Client-1, nslookup "search" observe the results of the CNAME record.


🎉Congratulation! You are done Building Instuition for DNS .!🎉 Next tutorial ,Network Files shares and permisssion by clicking [here](https://github.com/haleypruittcc/NetworkFilesSharesandPermission)

