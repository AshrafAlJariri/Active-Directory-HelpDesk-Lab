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

- <b>Active Directory Users and Computers (ADUC)</b> — Planned
- <b>Group Policy Management Console (GPMC)</b> — Planned
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

- I configured an Azure Virtual Network named **vnet-eastus-1** in the **East US** region using the **10.50.0.0/16** address space with two subnets to support my Windows Server environment.

- After that, I deployed a Windows Server virtual machine with the private IP address **10.50.1.4** and configured it without a directly assigned public IP address to reduce internet exposure.

<!-- Add a screenshot from Azure showing the VM overview, after hiding any account-specific identifiers. -->
<!-- ![Azure Windows Server VM](screenshots/01-azure-windows-server.png) -->
<!-- Caption: Deployed Windows Server 2025 in an Azure virtual network for the Active Directory Help Desk lab. -->

<h3>2. Point-to-Site VPN Setup</h3>

 <img src="https://i.imgur.com/oLZ4pKg.jpeg" height="80%" width="80%" /><br/>

- **VPN Setup**: I successfully connected my Windows 11 Pro workstation to the Azure Virtual Network using Azure VPN Client. To verify connectivity, I used the PowerShell Test-NetConnection command to test TCP port 3389 on the Windows Server's private IP address **(10.50.1.4).**
- **The test returned TcpTestSucceeded:** True, confirming that the Remote Desktop port was reachable through the VPN.

<h3>3.Active Directory Domain Services (AD DS) Installation</h3>
 <img src="https://i.imgur.com/c0QWbDY.jpeg" width="100%" /><br/>

- I installed **Active Directory Domain Services (AD DS)** on Windows Server 2025 Datacenter using Server Manager. After selecting the AD DS role, I completed the installation and confirmed it was successful. The server was then ready to be promoted to a domain controller.

<h3>4.Active Directory Forest Configuration and Prerequisite Validation</h3>
 <img src="https://i.imgur.com/JhJFXlc.png" width="100%" /><br/>

- I configured **Ashraf-DC-01** as a domain controller by selecting **Add a new forest** and specifying **corp.ashraflab.test** as the root domain name.

- I then ran the Active Directory prerequisite checks, which passed successfully with configuration warnings, allowing me to proceed with domain controller promotion.



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

<h3>1. Employee Accounts and Organizational Units — Planned</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
- Create OUs for departments and employees.
- Add test employee accounts and security groups.
- Configure group membership and employee account settings.
- Practice account onboarding and offboarding.

<h3>2. Windows 11 Domain Join — Planned</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
- Configure Windows 11 to use the domain controller for DNS over the VPN.
- Join the Windows 11 Pro workstation to the Active Directory domain.
- Verify domain sign-in and the computer object in Active Directory.

<h3>3. Help Desk Troubleshooting Scenarios — Planned</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
- <b>Forgotten Password:</b> Reset a test employee's password and verify successful sign-in.
- <b>Locked Account:</b> Investigate and unlock a test employee account.
- <b>Shared Folder Access:</b> Configure and test share and NTFS permissions.
- <b>Group Policy:</b> Apply and verify a workstation policy using <code>gpupdate /force</code> and <code>gpresult /r</code>.
- <b>DNS / Domain Sign-In:</b> Troubleshoot connectivity and name resolution as needed.

<h2>Screenshot Documentation</h2>

Screenshots will be stored in the <code>screenshots/</code> folder and added to each walkthrough section after capture. Images should show the actual configuration or verified result, with a one-sentence caption. Passwords, tokens, and private account details must not be shown.
<h2>Conclusion</h2>


<b>Project Status: In Progress</b>

So far, this lab has provided hands-on experience with deploying Windows Server in Microsoft Azure, configuring a private virtual network and Point-to-Site VPN, diagnosing network connectivity with PowerShell, and remotely administering the server using Windows 11 Pro in Parallels Desktop.

Upcoming work will focus on installing and configuring Active Directory Domain Services, joining a workstation to the domain, and performing practical Tier 1 Help Desk tasks involving employee accounts, Group Policy, and permissions.
