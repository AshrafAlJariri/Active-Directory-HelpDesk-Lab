
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
- <b>Windows Administrative Tools</b>

<h2>Environments Used</h2>

- <b>macOS</b> (Host Operating System)
- <b>Windows 11 Pro</b> (Client Virtual Machine)
- <b>Windows Server</b> (Planned Domain Controller)

<h2>Project Walk-through:</h2>

<h3>Objective 1: Active Directory Lab Environment Setup</h3>

<b>Goal:</b> Configure an Active Directory environment and connect a Windows 11 client to the domain.

<div align="center">

<p><b>Step 1: Verify Windows 11 system information using systeminfo</b></p>

<img src="images/01-system-information.png" width="80%" alt="Windows 11 System Information"/>

<br /><br />

<p><b>Step 2: Confirm Windows 11 is currently in a workgroup</b></p>

<img src="images/02-workgroup-verification.png" width="80%" alt="Windows 11 Workgroup Verification"/>

<br /><br />

<p><b>Step 3: Configure Active Directory Domain Services (Planned)</b></p>

<!-- Add screenshot after completing this step -->
<!-- <img src="images/03-active-directory-setup.png" width="80%" alt="Active Directory Setup"/> -->

<br /><br />

<p><b>Step 4: Verify Windows 11 domain connection (Planned)</b></p>

<!-- Add screenshot after completing this step -->
<!-- <img src="images/04-domain-connection.png" width="80%" alt="Domain Connection"/> -->

</div>

<h3>Objective 2: User Account Creation</h3>

<b>Goal:</b> Simulate onboarding a new employee by creating a user account in Active Directory.

<div align="center">

<p><b>Step 1: Open Active Directory Users and Computers</b></p>

<!-- <img src="images/05-aduc-console.png" width="80%" alt="ADUC Console"/> -->

<br /><br />

<p><b>Step 2: Create a new employee account</b></p>

<!-- <img src="images/06-create-user.png" width="80%" alt="Create User"/> -->

<br /><br />

<p><b>Step 3: Verify the employee account was created</b></p>

<!-- <img src="images/07-user-created.png" width="80%" alt="User Created"/> -->

</div>

<h3>Objective 3: Password Reset</h3>

<b>Goal:</b> Simulate a Help Desk ticket involving an employee who forgot their password.

<div align="center">

<p><b>Step 1: Locate the employee account in Active Directory</b></p>

<!-- <img src="images/08-locate-user.png" width="80%" alt="Locate User"/> -->

<br /><br />

<p><b>Step 2: Reset the employee password</b></p>

<!-- <img src="images/09-reset-password.png" width="80%" alt="Password Reset"/> -->

<br /><br />

<p><b>Step 3: Verify successful login using the new password</b></p>

<!-- <img src="images/10-password-login.png" width="80%" alt="Password Login"/> -->

</div>

<h3>Objective 4: Account Lockout Troubleshooting</h3>

<b>Goal:</b> Simulate an employee account lockout and restore account access.

<div align="center">

<p><b>Step 1: Identify the locked employee account</b></p>

<!-- <img src="images/11-account-locked.png" width="80%" alt="Account Locked"/> -->

<br /><br />

<p><b>Step 2: Unlock the account using Active Directory</b></p>

<!-- <img src="images/12-unlock-account.png" width="80%" alt="Unlock Account"/> -->

<br /><br />

<p><b>Step 3: Verify the employee can log in successfully</b></p>

<!-- <img src="images/13-account-unlocked.png" width="80%" alt="Account Unlocked"/> -->

</div>

<h3>Objective 5: Security Group Management</h3>

<b>Goal:</b> Create and manage Active Directory security groups to control employee access.

<div align="center">

<p><b>Step 1: Create a new security group</b></p>

<!-- <img src="images/14-create-group.png" width="80%" alt="Create Group"/> -->

<br /><br />

<p><b>Step 2: Add an employee to the security group</b></p>

<!-- <img src="images/15-add-user-group.png" width="80%" alt="Add User to Group"/> -->

<br /><br />

<p><b>Step 3: Verify the employee's group membership</b></p>

<!-- <img src="images/16-group-membership.png" width="80%" alt="Group Membership"/> -->

</div>

<h3>Objective 6: Windows Login Troubleshooting</h3>

<b>Goal:</b> Diagnose and resolve a simulated Windows domain login issue.

<div align="center">

<p><b>Step 1: Identify the Windows login issue</b></p>

<!-- <img src="images/17-login-error.png" width="80%" alt="Login Error"/> -->

<br /><br />

<p><b>Step 2: Troubleshoot the issue using Windows tools</b></p>

<!-- <img src="images/18-login-troubleshooting.png" width="80%" alt="Login Troubleshooting"/> -->

<br /><br />

<p><b>Step 3: Verify successful login after troubleshooting</b></p>

<!-- <img src="images/19-login-resolved.png" width="80%" alt="Login Resolved"/> -->

</div>

<h3>Objective 7: Group Policy Management</h3>

<b>Goal:</b> Configure and verify Group Policy settings in an Active Directory environment.

<div align="center">

<p><b>Step 1: Open Group Policy Management</b></p>

<!-- <img src="images/20-group-policy-console.png" width="80%" alt="Group Policy Console"/> -->

<br /><br />

<p><b>Step 2: Configure a Group Policy Object</b></p>

<!-- <img src="images/21-configure-gpo.png" width="80%" alt="Configure GPO"/> -->

<br /><br />

<p><b>Step 3: Verify Group Policy application</b></p>

<!-- <img src="images/22-verify-gpo.png" width="80%" alt="Verify GPO"/> -->

</div>

<h3>Objective 8: DNS and Network Troubleshooting</h3>

<b>Goal:</b> Troubleshoot network connectivity and DNS resolution issues using Windows command-line tools.

<div align="center">

<p><b>Step 1: Check network configuration using ipconfig</b></p>

<!-- <img src="images/23-ipconfig.png" width="80%" alt="IP Configuration"/> -->

<br /><br />

<p><b>Step 2: Troubleshoot DNS using nslookup and ping</b></p>

<!-- <img src="images/24-dns-troubleshooting.png" width="80%" alt="DNS Troubleshooting"/> -->

<br /><br />

<p><b>Step 3: Verify network connectivity after troubleshooting</b></p>

<!-- <img src="images/25-network-resolved.png" width="80%" alt="Network Resolved"/> -->

</div>

<h3>Objective 9: Employee Offboarding</h3>

<b>Goal:</b> Simulate an employee departure by disabling their Active Directory account and verifying access is restricted.

<div align="center">

<p><b>Step 1: Locate the employee account in Active Directory</b></p>

<!-- <img src="images/26-offboarding-user.png" width="80%" alt="Offboarding User"/> -->

<br /><br />

<p><b>Step 2: Disable the employee account</b></p>

<!-- <img src="images/27-disable-account.png" width="80%" alt="Disable Account"/> -->

<br /><br />

<p><b>Step 3: Verify the disabled account cannot authenticate</b></p>

<!-- <img src="images/28-account-disabled.png" width="80%" alt="Account Disabled"/> -->

</div>

<h2>Conclusion</h2>

This project is currently in progress. The completed lab will demonstrate practical experience with Microsoft Active Directory administration, user account management, password resets, account troubleshooting, security group management, Group Policy, and Windows networking.

Each objective will be documented with screenshots and verified troubleshooting results as the lab progresses.


<h2>Conclusion</h2>

This lab is designed to develop practical experience with Microsoft Active Directory and common IT Help Desk support tasks. Upon completion, the project will demonstrate user account administration, password and lockout troubleshooting, security group management, Group Policy configuration, network troubleshooting, and employee offboarding.

Each objective will be documented with screenshots and verified troubleshooting results to demonstrate hands-on technical skills.
