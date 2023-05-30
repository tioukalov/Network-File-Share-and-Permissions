<h1 align="center">Network File Sharing and Permissions</h1>
<p align="center"><img src="https://i.imgur.com/AeiqMDZ.png" height="15%" width="15%" alt="File Share image"/></p>

This tutorial demonstrates how files can be shared across a domain through AD security groups and permissions.

<h3>Environments and Technologies Used</h3>

- Active Directory
- Shared Network Files

<h3>Operating Systems Used</h3>

- Windows Server 2019 (Domain Controller)
- Windows 10 Pro (Client1)


<h2>Deployment and Configuration Steps</h2>

<p>Let's create a file we want to share on the domain controller's machine across the homelab.com domain to Client1's Windows 10 machine.</p>
<p><img src="https://i.imgur.com/S55ABgJ.png" height="50%" width="50%" alt="file and text creation"/></p>

<p>Let's share this file with a security group to make this lab more realistic at the corporate level. We can do so by navigating to the Server Manager's Active Directory Users and Computers under tools. We will create an Organizational Unit (OU) titled Security Group. In the security group OU we will create the Accounting Group. Inside the group properties, we will add ctioukalov, a user in the domain, into the group.</p>        
<p><img src="https://i.imgur.com/Q7CLt8W.png" height="49%" width="49%" alt="security group creation"/>
   <img src="https://i.imgur.com/a1HDID4.png" height="29%" width="29%" alt="adding ctioukalov"/>
</p>

<p>Now, let's right click on the Accounting folder on the desktop and click on properties. We will select the sharing tab on the top and click on share.... Now, we will search for the Accounting Group and enable read permissions. Note the network path in the Accounting folder properties in the screenshot above: \\DCHOMELAB\. We will refer to this later in the lab.</p>
<p><img src="https://i.imgur.com/IqjEGaI.png" height="49%" width="49%" alt="1"/>
   <img src="https://i.imgur.com/XsSBTcK.png" height="49%" width="49%" alt="2"/>
</p>

<p>Next, we have to enable read permissions in advanced sharing settings.</p>
<p><img src="https://i.imgur.com/zChmvnr.png" height="50%" width="50%" alt="3"/></p>   

<p>Now, let's see if we are able to access the Accounting folder as ctioukalov, who we just added to the Accounting Group. After logging into ctioukalov, we must ensure network discovery and file sharing is enabled on Client1's Network tab in file explorer.</p>
<p><img src="https://i.imgur.com/driPeFc.png" height="49%" width="49%" alt="logging into ctioukalov"/>
   <img src="https://i.imgur.com/rE8mugF.png" height="49%" width="49%" alt="network discovery"/>
</p>

<p>Noting the Accounting network file path from earlier, \\DCHOMELAB\, let's search it in the network search bar.</p>
<p><img src="https://i.imgur.com/VPOUs3n.png   " height="50%" width="50%" alt="success"/></p>  

<p>YAY! As you can see, we now can read the 2023 Accounting .txt file inside the Accounting Folder, which originated from another machine in the domain.</p>

<p>Lastly, we should check if non-Accounting Group members are denied access to the folder. Now let's log in with Peter Pan's domain credentials.</p>
<p><img src="https://i.imgur.com/2Lbv1de.png" height="50%" width="50%" alt="ppan access attempt"/></p>  
<p>Excellent! Peter Pan does not have the proper permissions to read the file. </p><br><br>

<p>Thank you for your time!</p>
