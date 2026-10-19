
<h1>Active Directory Help Desk Lab</h1>

<h2>Description</h2>
This project focuses on simulating real-world IT Help Desk tasks using Microsoft Active Directory in a Windows environment. The lab covers user account management, password resets, account lockouts, security group management, login troubleshooting, Group Policy, DNS troubleshooting, and employee offboarding.

The purpose of this project is to develop hands-on experience with common Tier 1 Help Desk responsibilities, including resolving user access issues, managing accounts, and troubleshooting Windows domain environments.
<br />

<h2>Languages and Utilities Used</h2>

- <b>Active Directory Users and Computers (ADUC)</b>
- <b>Group Policy Management Console (GPMC)</b>
- <b>Windows PowerShell</b>
- <b>Command Prompt</b>
- <b>VMware Fusion</b>
- <b>UTM</b>
- <b>Windows Administrative Tools</b>

<h2>Environments Used</h2>

- <b>macOS</b> (Host Operating System)
- <b>VMware Fusion - Windows 11 Pro</b> (Client Virtual Machine)
- <b>UTM - Windows Server 2025 Evaluation</b> (Domain Controller)

<h2>Project Walk-through:</h2>

<h3>Objective 1: Active Directory Lab Environment Setup</h3>

<b>Goal:</b> Configure an Active Directory environment and connect a Windows 11 client to the domain.

<p align="center">
Verify Windows 11 domain connection: <br/>
<!-- Screenshot: Successful domain join -->
<img src="https://imgur.com/ZopUocF.png" height="80%" width="80%" alt="Domain Connection"/>
<br />
I verified that the Windows 11 computer was initially part of a workgroup rather than an Active Directory domain. This established its starting configuration before the domain join.
<br/><br/>
Configure Windows Server 2025 using UTM: <br/>
<img src="https://i.imgur.com/xT1thkY.png" height="80%" width="80%"/>
<br/>
I configured a <b>Windows Server 2025</b> virtual machine using <b>UTM</b> with <b>4 GB RAM</b>, <b>4 CPU cores</b>, and <b>64 GB storage</b> to establish the server environment for my Active Directory lab.
<br/><br/>
<b>3. Active Directory Domain Configuration:</b>
<br/>
<img src="https://i.imgur.com/4eY5e9f.png" height="80%" width="80%" alt="Active Directory Domain Configuration"/>
<br/>

I installed **Windows Server 2025 Standard Evaluation (Desktop Experience)** using **UTM** and verified that **Server Manager** launched successfully. This server will be configured as a **Domain Controller** for my **Active Directory Help Desk Lab**.

<br/><br/>
<b> 4. Windows 11 Domain Join Verification:</b>
<br/>
<img src="images/04-domain-join.png" height="80%" width="80%" alt="Windows 11 Domain Join"/>
<br/>
I joined the <b>Windows 11 Pro</b> client running in <b>VMware Fusion</b> to the <b>Active Directory domain</b>, simulating the process of connecting an employee workstation to a corporate network.
<br/>
<br/>
  
</p>

<h3>Objective 2: User Account Creation</h3>

<b>Goal:</b> Simulate onboarding a new employee by creating a user account in Active Directory.

<p align="center">
Open Active Directory Users and Computers: <br/>
<img src="https://images/04-aduc-console.png" height="80%" width="80%" alt="ADUC Console"/>
<br />
<br />
Create a new employee account: <br/>
<img src="images/05-create-user.png" height="80%" width="80%" alt="Create User"/>
<br />
<br />
Verify the employee account was created: <br/>
<img src="images/06-user-created.png" height="80%" width="80%" alt="User Created"/>
<br />
<br />
</p>

<h3>Objective 3: Password Reset</h3>

<b>Goal:</b> Simulate a Help Desk ticket involving an employee who forgot their password.

<p align="center">
Locate the employee account in Active Directory: <br/>
<img src="images/07-locate-user.png" height="80%" width="80%" alt="Locate User"/>
<br />
<br />
Reset the employee password: <br/>
<img src="images/08-reset-password.png" height="80%" width="80%" alt="Password Reset"/>
<br />
<br />
Verify successful login using the new password: <br/>
<img src="images/09-password-login.png" height="80%" width="80%" alt="Password Login"/>
<br />
<br />
</p>

<h3>Objective 4: Account Lockout Troubleshooting</h3>

<b>Goal:</b> Simulate an employee account lockout and restore account access.

<p align="center">
Identify the locked employee account: <br/>
<img src="images/10-account-locked.png" height="80%" width="80%" alt="Account Locked"/>
<br />
<br />
Unlock the account using Active Directory: <br/>
<img src="images/11-unlock-account.png" height="80%" width="80%" alt="Unlock Account"/>
<br />
<br />
Verify the employee can log in successfully: <br/>
<img src="images/12-account-unlocked.png" height="80%" width="80%" alt="Account Unlocked"/>
<br />
<br />
</p>

<h3>Objective 5: Security Group Management</h3>

<b>Goal:</b> Create and manage Active Directory security groups to control employee access.

<p align="center">
Create a new security group: <br/>
<img src="images/13-create-group.png" height="80%" width="80%" alt="Create Group"/>
<br />
<br />
Add an employee to the security group: <br/>
<img src="images/14-add-user-group.png" height="80%" width="80%" alt="Add User to Group"/>
<br />
<br />
Verify the employee's group membership: <br/>
<img src="images/15-group-membership.png" height="80%" width="80%" alt="Group Membership"/>
<br />
<br />
</p>

<h3>Objective 6: Windows Login Troubleshooting</h3>

<b>Goal:</b> Diagnose and resolve a simulated Windows domain login issue.

<p align="center">
Identify the Windows login issue: <br/>
<img src="images/16-login-error.png" height="80%" width="80%" alt="Login Error"/>
<br />
<br />
Troubleshoot the issue using Windows tools: <br/>
<img src="images/17-login-troubleshooting.png" height="80%" width="80%" alt="Login Troubleshooting"/>
<br />
<br />
Verify successful login after troubleshooting: <br/>
<img src="images/18-login-resolved.png" height="80%" width="80%" alt="Login Resolved"/>
<br />
<br />
</p>

<h3>Objective 7: Group Policy Management</h3>

<b>Goal:</b> Configure and verify Group Policy settings in an Active Directory environment.

<p align="center">
Open Group Policy Management: <br/>
<img src="images/19-group-policy-console.png" height="80%" width="80%" alt="Group Policy Console"/>
<br />
<br />
Configure a Group Policy Object: <br/>
<img src="images/20-configure-gpo.png" height="80%" width="80%" alt="Configure GPO"/>
<br />
<br />
Verify Group Policy application: <br/>
<img src="images/21-verify-gpo.png" height="80%" width="80%" alt="Verify GPO"/>
<br />
<br />
</p>

<h3>Objective 8: DNS and Network Troubleshooting</h3>

<b>Goal:</b> Troubleshoot network connectivity and DNS resolution issues using Windows command-line tools.

<p align="center">
Check network configuration using ipconfig: <br/>
<img src="images/22-ipconfig.png" height="80%" width="80%" alt="IP Configuration"/>
<br />
<br />
Troubleshoot DNS using nslookup and ping: <br/>
<img src="images/23-dns-troubleshooting.png" height="80%" width="80%" alt="DNS Troubleshooting"/>
<br />
<br />
Verify network connectivity after troubleshooting: <br/>
<img src="images/24-network-resolved.png" height="80%" width="80%" alt="Network Resolved"/>
<br />
<br />
</p>

<h3>Objective 9: Employee Offboarding</h3>

<b>Goal:</b> Simulate an employee departure by disabling their Active Directory account and verifying access is restricted.

<p align="center">
Locate the employee account in Active Directory: <br/>
<img src="images/25-offboarding-user.png" height="80%" width="80%" alt="Offboarding User"/>
<br />
<br />
Disable the employee account: <br/>
<img src="images/26-disable-account.png" height="80%" width="80%" alt="Disable Account"/>
<br />
<br />
Verify the disabled account cannot authenticate: <br/>
<img src="images/27-account-disabled.png" height="80%" width="80%" alt="Account Disabled"/>
<br />
<br />
</p>

<h2>Conclusion</h2>

This lab is designed to develop practical experience with Microsoft Active Directory and common IT Help Desk support tasks. Upon completion, the project will demonstrate user account administration, password and lockout troubleshooting, security group management, Group Policy configuration, network troubleshooting, and employee offboarding.

Each objective will be documented with screenshots and verified troubleshooting results to demonstrate hands-on technical skills.
