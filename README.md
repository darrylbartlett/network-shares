<p align="center">
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/f3dd7112-ad2b-471c-9348-6c6ecac61e27)"/>
</p>

<h1>Network File Shares and Permissions</h1>
This is a brief tutorial outlining shared permissions on a network.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure for creating Virtual Machines

<h2>Operating System Used</h2>

- Windows Server 2022 for a domain controller
- Windows 10 Pro (22H2) for a client computer

<h2>List of Prerequisites</h2>

- Creation of an Azure Virtual Machine (VM) with Windows 10 Pro as a client computer
- Creation of an Azure Virtual Machine (VM) with Windows Server 2022 as a domain controller
- Connecting to the VMs using Remote Desktop Connection with their created public IPs, usernames and passwords
<br />


<h2>Create file shares with different permissions</h2>

<p>Login to the domain controller with your admin account. On the domain controller, create 4 folders on the C: drive:</p>

- Read-access
- Write-access
- No-access
- Accounting

<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/add5fc82-ed24-47ca-8a9f-db2f4177a891"/>
</p>
<br />



<p>Use the following criteria to setup Share permissions for Domain Users:</p>

- Read-access folder - Read permission
- Write-access folder – Read/Write permissions
- No-access folder – access given only to Domain Admins with Read/Write permissions

<p>Right-click on each folder and select Properties.</p>
<p>Select the Sharing tab in the Properties window.</p>
<p>Click the Share… button.</p>
<p>Type in Domain Users and click the Add button. For the No-access folder, type in Domain Admins, not Domain Users.</p>

<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/96b8ea19-8401-48a9-8832-fe64e2226e82"/>
</p>
<br />



