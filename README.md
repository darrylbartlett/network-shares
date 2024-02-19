<p align="center">
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/f3dd7112-ad2b-471c-9348-6c6ecac61e27)"/>
</p>

<h1>Network File Shares and Permissions</h1>
<p>This is a brief tutorial outlining shared permissions on a network.</p>
<p>This tutorial continues from the Active Directory tutorial.</p><br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure for creating Virtual Machines

<h2>Operating System Used</h2>

- Windows Server 2022 for a domain controller
- Windows 10 Pro (22H2) for a client computer

<h2>List of Prerequisites</h2>

- Creation of an Azure Virtual Machine (VM) with Windows 10 Pro as a client computer
- Creation of an Azure Virtual Machine (VM) with Windows Server 2022 as a domain controller
- Connecting to the VMs using Remote Desktop Connection with their created public IPs, usernames and passwords
- Logged in as an Admin user on the Domain Controller computer.
- From the Active Directory tutorial, you have the user John Doe logged in as a normal user on the Client computer.
<br />


<h2>Create File Shares with Different Permissions</h2>

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

- Read-access folder – Read permission
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

<h2>Read-access Folder with Read Permission</h2>

<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/63497466-d42c-4c17-868f-eb59da5aecac"/>
</p>
<br />
<p>Click the Share button. Click Done. Click Close.</p>

<h2>Write-access Folder with Read/Write Permissions</h2>

<p>Here is the Write-access folder with Domain Users added and the default Read permissions.</p>
<p>This folder should have Read/Write permissions.</p>
<p>Click on the reversed triangle and select Read/Write from the list.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/9c43d74f-c5ad-4586-95e9-bc1c944e7367"/>
</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/2e619734-a2df-4041-b811-40eb6a18ebe2"/>
</p>
<br />
<p>Click the Share button. Click Done. Click Close.</p>

<h2>No-access Folder with Read/Write Permissions for Domain Admins</h2>

<p>Here’s the No-access folder with Domain Admins and Read/Write permissions. Domain Users have no access to this folder.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/0ff2a801-6b9a-41ce-866d-79518d53c3e3"/>
</p>
<br />

<h2>Test the File Share Access with a Normal User Account</h2>

<p>Go to the Client computer.</p>
<p>Remember: John Doe (john_user) should already be logged in.</p>
<p>Open File Explorer and type in \\dc-1 as the path.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/c58e4b34-82f9-4de7-830c-d6683e18a6ec"/>
</p>
<br />

<p>Try to access each of the folders that were created and shared:</p>

- Try to add a document to the Read-access folder. As a normal user, you shouldn’t be able to add a document to a Read only folder.</p>

<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/0b6a56fe-d947-4f80-b540-6166281bd31b"/>
</p>
<br />

- Try to add a document to the Write-access folder. As a normal user, you should be able to add a document to a Read/Write folder.
- Try to access the No-access folder. This folder is for Domain Admins, so you should see an access error when trying to open it.

<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/4c264d34-4545-43ec-983f-c9c5a2c5047f"/>
</p>
<br />

<h2>Adding an ACCOUNTANTS Security Group</h2>

<p>Go back to the domain controller.</p>
<p>In Active Directory Users and Computers, create a new security group.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/0ad6a22d-de97-4ffa-8bff-f347c5efd825"/>
</p>
<br />

<p>For the Group name, enter ACCOUNTANTS. Click OK.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/13b64f5e-2f33-46d0-b77a-1adf83477176"/>
</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/d73a57ab-10c6-47cf-86a1-b8fbedca2c8e"/>
</p>
<br />

<p>Go to the Accounting folder created earlier.</p>
<p>Right-click the folder and go to the Properties. Share it with the ACCOUNTANTS group using Read/Write permissions.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/076465b4-20c2-4351-a2f3-eaa97b165616"/>
</p>
<br />

<p>A normal user like John Doe, who is not a part of the ACCOUNTANTS group, will not be able to access the Accounting folder.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/fb0caacd-2808-4f7f-9657-2b5219cb0a76"/>
</p>
<br />

<p>If we add John Doe to the ACCOUNTANTS security group, the access will change.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/2bf41ccb-2bd2-4dec-864c-14bd589be328"/>
</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/318a1e8a-1cd7-4f0b-b060-284630cfdc35"/>
</p>
<br />

<p>Log out John Doe on the Client computer and log him back in.</p>
<p>Go ahead and access the Accounting folder at \\dc-1 in File Explorer, and add a document.</p>
<p>
<img src="https://github.com/darrylbartlett/network-shares/assets/159499839/6487721b-3452-4bd2-b583-4e698465324d"/>
</p>
<br />






