<h1>Active Directory Help Desk Lab</h1>

<h2>Description</h2>

This project focuses on simulating real-world IT Help Desk tasks using Microsoft Active Directory in a Windows environment. The lab covers user account management, password resets, account lockouts, security group management, login troubleshooting, Group Policy, DNS troubleshooting, and employee onboarding.

The lab uses <b>Windows Server 2025</b> hosted in <b>Microsoft Azure</b> and <b>Windows 11 Pro</b> running locally on a MacBook through <b>Parallels Desktop</b>. An Azure Point-to-Site VPN connects the Windows 11 workstation to the private Azure network. Remote Desktop is used to administer the server.

The purpose of this project is to gain hands-on experience with common Tier 1 Help Desk responsibilities, including resolving user access issues, managing accounts, and troubleshooting Windows domain environments.
<h2>Objectives</h2>

- Configure a Windows Server virtual machine and private network in Microsoft Azure.
- Connect Windows 11 Pro to Azure using a Point-to-Site VPN.
- Remotely administer Windows Server using Remote Desktop.
- Install Active Directory Domain Services (AD DS) and configure a domain controller.
- Create and organize employee user accounts, groups, and organizational units (OUs).
- Join a Windows 11 Pro workstation to the Active Directory domain.
- Practice password resets, account unlocking, and employee onboarding/offboarding.
- Configure shared folder access and NTFS permissions.
- Apply and troubleshoot Group Policy Objects (GPOs).
- Document troubleshooting and verification steps with screenshots.
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
<h2>Walkthrough</h2>

<h3>1. Azure Virtual Network and Windows Server Deployment — Completed</h3>
 <img src="https://i.imgur.com/zeeOYGF.png" height="80%" width="80%" /><br/>

- Created an Azure virtual network named <b>vnet-eastus-1</b>.
- Configured the server subnet <b>10.50.1.0/24</b> and a dedicated GatewaySubnet.
- Deployed a Windows Server 2025 Datacenter virtual machine named <b>Ashraf-DC-01</b> in East US.
- Configured the server with the private IP address <b>10.50.1.4</b>.
- Kept the server without a directly assigned public IP address.

<!-- Add a screenshot from Azure showing the VM overview, after hiding any account-specific identifiers. -->
<!-- ![Azure Windows Server VM](screenshots/01-azure-windows-server.png) -->
<!-- Caption: Deployed Windows Server 2025 in an Azure virtual network for the Active Directory Help Desk lab. -->

<h3>2. Point-to-Site VPN Setup — Completed</h3>

 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
- Deployed the Azure VPN Gateway.
- Configured Point-to-Site VPN access using OpenVPN and Microsoft Entra ID authentication.
- Downloaded the Azure VPN client configuration profile.
- Installed Azure VPN Client on Windows 11 Pro in Parallels Desktop.
- Imported the profile and successfully connected to <b>vnet-eastus-1</b>.

<!-- ![VPN connected](screenshots/02-azure-vpn-connected.png) -->
<!-- Caption: Connected the Windows 11 client to the Azure virtual network using Azure VPN Client. -->

<h3>3. VPN Connectivity Troubleshooting — Completed</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
Initial ICMP ping attempts to the Azure server timed out. To verify whether the server was reachable over the VPN, I inspected the IPv4 route table and tested TCP connectivity to Remote Desktop port 3389.
route print -4
Test-NetConnection 10.50.1.4 -Port 3389
The PowerShell test returned:
RemoteAddress    : 10.50.1.4
RemotePort       : 3389
InterfaceAlias   : vnet-eastus-1
SourceAddress    : 172.16.100.2
TcpTestSucceeded : True
<b>Result:</b> Confirmed TCP access to the Windows Server RDP port over the VPN. The exact reason ICMP ping did not respond was not determined.
<!-- ![VPN TCP connectivity](screenshots/03-vpn-connectivity-test.png) -->
<!-- Caption: Verified that the Windows 11 client could reach Windows Server over the Azure VPN on TCP port 3389. -->

<h3>4. Remote Desktop to Windows Server — Completed</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
- Opened Remote Desktop Connection (<code>mstsc</code>) on Windows 11.
- Connected to the server's private IP address, <b>10.50.1.4</b>.
- Signed in using the server administrator account.
- Successfully opened Windows Server 2025 and <b>Server Manager</b> through Remote Desktop.
<!-- ![Windows Server Manager](screenshots/04-windows-server-manager.png) -->
<!-- Caption: Accessed the Azure-hosted Windows Server 2025 desktop remotely from the Windows 11 client. -->

<h3>5. Active Directory Domain Services — In Progress</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
Next steps:
1. In Server Manager, open <b>Manage > Add Roles and Features</b>.
2. Install <b>Active Directory Domain Services (AD DS)</b>.
3. Promote the server to a domain controller and configure a new forest/domain.
4. Verify DNS and Active Directory administration tools.
<!-- Add a screenshot only after AD DS installation is actually complete. -->

<h3>6. Employee Accounts and Organizational Units — Planned</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
- Create OUs for departments and employees.
- Add test employee accounts and security groups.
- Configure group membership and employee account settings.
- Practice account onboarding and offboarding.
<h3>7. Windows 11 Domain Join — Planned</h3>
 <img src="https://imgur.com/Uce9jX4.png" height="80%" width="80%" /><br/>
- Configure Windows 11 to use the domain controller for DNS over the VPN.
- Join the Windows 11 Pro workstation to the Active Directory domain.
- Verify domain sign-in and the computer object in Active Directory.

<h3>8. Help Desk Troubleshooting Scenarios — Planned</h3>
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
