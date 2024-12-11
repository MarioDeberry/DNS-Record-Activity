<p align="center">
  <img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

# DNS Records
In this tutorial, we create and observe (A) and CNAME records.

## Environments and Technologies Used
- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop**
- Various **Command-Line Tools**

## Operating Systems Used
- **Windows 10** (21H2)
- **Ubuntu Server 20.04**

## High-Level Steps
- **A-Record** Creation and Observation
- **DNS Cache** Flush
- **CNAME Record** Creation and Observation

## Actions and Observations

### 1. A-Record Creation and Observation
<p>
  <img src="https://github.com/chrisrraP/azure-network-protocols/blob/main/Ping%20Host%20From%20Client%20Fail.png" height="80%" width="80%" alt="Ping Host Fail"/>
</p>
<p>
  <img src="https://github.com/chrisrraP/azure-network-protocols/blob/main/Create%20A-record.png" height="80%" width="80%" alt="Create A-record"/>
</p>
<p>
  <img src="https://github.com/chrisrraP/azure-network-protocols/blob/main/Ping%20to%20Host%20Success.png" height="80%" width="80%" alt="Ping Host Success"/>
</p>
Create a virtual server and one client with Microsoft Azure. Reference [Configuring Active Directory](https://github.com/chrisrraP/configure-ad) to learn how to create virtual machines.  
Log into the client and ping a record that has not yet been created. Using the domain server, create an **A-record** in the DNS Manager.  
Pinging the record name again from the client VM will show it now exists in the DNS cache.

### 2. DNS Cache Flush
<p>
  <img src="https://github.com/chrisrraP/Record-Creation-and-Observation/blob/main/DNS%20Flush%20Results.png" height="80%" width="80%" alt="DNS Flush Results"/>
</p>
Using the domain server, change the host record's IP address. When pinging from the client machine, the old address will show.  
As an administrator, open the command prompt and enter (ipconfig/flushdns). Ping again and the new address will show up in the refreshed cache.

### 3. CNAME Record Creation and Observation
<p>
  <img src="https://github.com/chrisrraP/Record-Creation-and-Observation/blob/main/Cname%20Created.png" height="80%" width="80%" alt="CNAME Created"/>
</p>
<p>
  <img src="https://github.com/chrisrraP/Record-Creation-and-Observation/blob/main/NSlookup%20Cname.png" height="80%" width="80%" alt="NSlookup CNAME"/>
</p>
Create a (CNAME record) using the domain server that uses the host name "search" to reach out to "www.google.com".  
Ping "search" from the client VM and observe results.  
Use the command `nslookup search` in the command prompt to display additional address information.
