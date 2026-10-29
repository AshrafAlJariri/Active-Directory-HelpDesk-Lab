<h1>Active Directory Help Desk Lab</h1>

<h2>Description</h2>

This project demonstrates how I built and administered a Microsoft Active Directory environment using Windows Server hosted in Microsoft Azure. I configured Azure networking, established a Point-to-Site VPN connection, installed Active Directory Domain Services (AD DS), and created a domain to simulate a real-world business environment.

After setting up the environment, I focused on performing common Active Directory administrative tasks, including creating employee accounts, managing security groups, modifying user properties, resetting passwords, managing user lifecycles, and examining Group Policy Objects (GPOs). These tasks simulate day-to-day responsibilities performed by IT Help Desk and IT Support professionals.

The project is divided into two parts:

- **Part 1 – Environment Setup:** Configuring Azure networking, VPN connectivity, Windows Server, and Active Directory Domain Services (AD DS).

- **Part 2 – Active Directory Administration:** Demonstrating common administrative tasks, including user account creation, security group management, user property modification, password resets, user lifecycle management, and Group Policy Object (GPO) examination.

The purpose of this project is to gain hands-on experience with common Tier 1 Help Desk responsibilities, including resolving user access issues, managing accounts, and troubleshooting Windows domain environments.
<h2>Objectives</h2>

- **User Account Creation:** Create new employee accounts with unique usernames, full names, and initial passwords to simulate employee onboarding.

- **Adding Users to Security Groups:** Assign users to appropriate security groups based on their departments and job responsibilities to manage access permissions.

- **User Property Modification:** Update existing user properties, including department information, contact details, and account settings.

- **Group Management:** Create and manage security groups, assign descriptive names, and organize group memberships to support access control.

- **User Lifecycle Management:** Disable and delete test user accounts to simulate employee offboarding and maintain account security.

- **Group Policy Object (GPO) Examination:** Explore existing Group Policy Objects to understand how password policies, desktop configurations, and software deployment settings are managed..

<h2>Languages and Utilities Used</h2>

- <b>Active Directory Users and Computers (ADUC)</b> 
- <b>Group Policy Management Console (GPMC)</b>
- <b>Windows PowerShell</b>
- <b>Command Prompt</b>
- <b>Remote Desktop Connection (RDP)</b>
- <b>Azure VPN Client</b>
- <b>Azure Portal</b>
- <b>Windows Administrative Tools / Server Manager</b>
<h2>Environments Used</h2>

- <b>macOS</b> — Host operating system
- <b>Parallels Desktop</b> — Runs the Windows 11 Pro client virtual machine
- <b>Windows 11 Pro</b> — Employee / Help Desk client workstation
- <b>Microsoft Azure</b> — Cloud environment hosting Windows Server
- <b>Windows Server 2025 Datacenter</b> — Azure-hosted server (Ashraf-DC-01)
- <b>Azure Virtual Network</b> — 10.50.0.0/16, with server subnet 10.50.1.0/24
- <b>Azure VPN Gateway</b> — Point-to-Site remote network access
<h2>Lab Architecture</h2>

MacBook (macOS)
   |
Parallels Desktop
   |
Windows 11 Pro (Client Workstation)
   |
Azure VPN Client (Point-to-Site VPN)
   |
Azure VPN Gateway
   |
Azure Virtual Network (10.50.0.0/16)
   |
Server Subnet (10.50.1.0/24)
   |
Azure Windows Server 2025 (Ashraf-DC-01, 10.50.1.4)
   |
Active Directory Domain Services (installation pending)
<b>Important:</b> Parallels runs the Windows 11 client, not the domain controller. Windows Server runs in Azure. Remote Desktop on Windows 11 controls the Azure server through the VPN.
<h2>Setup-Walkthrough</h2>

<h3>1. Azure Virtual Network and Windows Server Deployment</h3>
 <img src="https://i.imgur.com/nIFMAns.jpeg" height="80%" width="80%" /><br/>

<p align="center">
  <strong>Azure Virtual Network and Windows Server Deployment:</strong> I configured an Azure Virtual Network named <strong>vnet-eastus-1</strong> in the East US region using the <strong>10.50.0.0/16</strong> address space with two subnets. I then deployed a Windows Server virtual machine with the private IP address <strong>10.50.1.4</strong> and no directly assigned public IP address to reduce internet exposure.
</p>

<h3>2. Point-to-Site VPN Setup</h3>

 <img src="https://i.imgur.com/oLZ4pKg.jpeg" height="80%" width="80%" /><br/>

<p align="center">
  <strong>VPN Setup and Connectivity Verification:</strong> I connected my Windows 11 Pro workstation to the Azure Virtual Network using Azure VPN Client. I then used the PowerShell <strong>Test-NetConnection</strong> command to test TCP port 3389 on the Windows Server's private IP address (10.50.1.4). The test returned <strong>TcpTestSucceeded: True</strong>, confirming that the Remote Desktop port was reachable through the VPN.
</p>


<h3>3.Active Directory Domain Services (AD DS) Installation</h3>
 <img src="https://i.imgur.com/c0QWbDY.jpeg" width="100%" /><br/>

<p align="center">
  <strong>Active Directory Domain Services (AD DS) Installation:</strong> I installed Active Directory Domain Services (AD DS) on Windows Server 2025 Datacenter using Server Manager. After selecting the AD DS role, I completed the installation and verified that it was successful. The server was then ready to be promoted to a domain controller.
</p>


<h3>4.Active Directory Forest Configuration and Prerequisite Validation</h3>
 <img src="https://i.imgur.com/JhJFXlc.png" width="100%" /><br/>

<p align="center">
  <strong>Active Directory Forest Configuration:</strong> I configured Ashraf-DC-01 as a domain controller by selecting <strong>Add a new forest</strong> and specifying <strong>corp.ashraflab.test</strong> as the root domain name. I then ran the Active Directory prerequisite checks, which passed successfully with configuration warnings, allowing me to proceed with domain controller promotion.
</p>

<h3>5. Remote Desktop to Windows Server</h3>
 <img src="https://i.imgur.com/9oKlEbM.jpeg"  width="100%" /><br/>

<p align="center">
<strong>Remote Desktop (RDP) Connection:</strong> I established a Remote Desktop connection from my Windows 11 Pro workstation to the Azure-hosted Windows Server using its private IP address <b>(10.50.1.4).</b> I then accessed Server Manager to remotely administer and configure the server.
</p>




<h3>6.Active Directory Domain and Windows 11 Domain Join Verification</h3>
 <img src="https://i.imgur.com/svbhajN.jpeg"  width="100%" /><br/>
<p align="center">
<strong>Domain and Workstation Verification:</strong> I verified that my Active Directory domain, corp.ashraflab.test, was accessible and that Ashraf-DC-01 was listed as the domain controller. I also confirmed that my Windows 11 Pro workstation (CLIENT-01) was successfully joined to the domain.
</p>

<h2>Part 2: Active Directory Administration Walkthrough</h2>

<h3>Objective 1. User Account Creation and Department Organization</h3>
 <img src="https://i.imgur.com/4G7wkdy.jpeg" width="100%" /><br/>
 <img src="https://i.imgur.com/5nW5eh2.jpeg" width="100%" /><br/>
<p align="center">
  <strong>User Account Creation:</strong> I created eight employee user accounts in Active Directory and organized them into four departments: IT, HR, Finance, and Sales. Each department contains two user accounts, simulating the process of onboarding new employees and organizing users within their respective Organizational Units (OUs).
</p>

<h3>Objective 2. User Property Modification</h3>
 <img src="https://i.imgur.com/Iu45ZCr.png" width="100%" /><br/>
<p align="center">
  <strong>User Property Modification:</strong> I modified an existing user account in Active Directory, such as updating a user's department, contact information, and account settings. For example, I updated John Smith's job title, department, and company information. I then saved the changes and verified that the updated properties were successfully applied. This demonstrated my ability to perform routine account maintenance. 
</p>


<h3>Objective 3. Security Group Management. </h3>

<p align="center"><strong>Security Group Creation</strong></p>
<p align="center">
  <img src="https://i.imgur.com/FP8IzHW.png" width="600" alt="Security Group Creation">
</p>
<p align="center"><strong>Adding Users and Verifying Group Membership</strong></p> 
 <img src="https://i.imgur.com/VrHjQ9K.png" width="100%" /><br/>
 <p align="center">
  <strong>Security Group Management:</strong> I created a Global Security Group named GG_IT_Users within the IT organizational unit. I then added John Smith and Sara James to the group and verified their membership to demonstrate how Active Directory security groups are used to organize users and manage access permissions.
</p>

<h3>Objective 4. User Lifecycle Management</h3>
<p align="center"><strong>User Account Creation</strong></p>
 <img src="https://i.imgur.com/pl87pkh.png" width="100%" /><br/>
<p align="center"><strong>Resetting User Account</strong></p>
  <img src="https://i.imgur.com/RVWBuwk.png" width="100%" /><br/>
 <p align="center"><strong>Account Disabling</strong></p>
 <img src="https://i.imgur.com/WYM8BtY.png" width="100%" /><br/>
 <p align="center"><strong>Account Re-enabling</strong></p>
 <img src="https://i.imgur.com/VLCN1VR.png" width="100%" /><br/>
<p align="center"><strong>Account Deletion</strong></p>
 <img src="https://i.imgur.com/R63cAEy.png" width="100%" /><br/>
<p align="center">
  <strong>User Lifecycle Management:</strong> I created a test employee account named Michael Davis in the IT department to simulate employee onboarding. I then practiced disabling and re-enabling the account to manage user access. Finally, I simulated employee offboarding by deleting the account from Active Directory.
</p>

<h3>Objective 5. Group Policy Object (GPO) Configuration and Verification</h3>
 <p align="center"><strong>GPO Creation and Linking</strong></p>
 <img src="https://i.imgur.com/Z1wDAh8.jpeg" width="100%" /><br/>
<p align="center"><strong>GPO Configuration</strong></p>
 <img src="https://i.imgur.com/481m4d4.png" width="100%" /><br/>
<p align="center"><strong>Policy Update and Verification</strong></p>
 <img src="https://i.imgur.com/exIhsd1.jpeg" width="100%" /><br/>
<p align="center"><strong>Group Policy Application</strong></p>
 <img src="https://i.imgur.com/U0Tr3yg.jpeg" width="100%" /><br/>
<p align="center"><strong>Restriction Testing</strong></p>
 <img src="https://i.imgur.com/JqupWr3.jpeg" width="100%" /><br/>
     <p align="center">
  <strong>Group Policy Management:</strong> I created and configured a Group Policy Object named IT-Workstation-Policy to restrict access to Control Panel and PC Settings for IT users. I then applied the policy using gpupdate /force and verified its application using gpresult /r. Finally, I tested the restriction on the Windows 11 workstation.
</p>


<h2>What I Learned</h2>

<p>
Through this project, I gained hands-on experience building and managing an Active Directory environment using Microsoft Azure and Windows Server 2025. I learned how to configure virtual networking, establish secure VPN connectivity, deploy a domain controller, and join a Windows 11 workstation to a domain.
</p>

<p>
I also developed practical Active Directory administration skills, including creating and organizing user accounts, managing Organizational Units (OUs), modifying user properties, configuring security groups, and performing user lifecycle management. Additionally, I gained experience creating, applying, and verifying Group Policy Objects (GPOs).
</p>

<p>
Overall, this project strengthened my understanding of Windows domain administration, user access management, and the fundamental skills required for entry-level IT Help Desk and System Administration roles.
</p>

