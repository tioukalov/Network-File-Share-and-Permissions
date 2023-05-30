<h1 align="center">Network File Sharing and Permissions</h1>
<p align="center"><img src="https://i.imgur.com/AeiqMDZ.png" height="15%" width="15%" alt="File Share image"/></p>

This tutorial demenstrates how files can be shared across a domain through AD security groups and permissions.

<h3>Environments and Technologies Used</h3>

- Active Directory
- Shared Network Files

<h3>Operating Systems Used</h3>

- Windows Server 2019 (Domain Controller)
- Windows 10 Pro (Client1)


<h2>Deployment and Configuration Steps</h2>

<p>On the domain controller's machine, let's create a file we want to share across the homelab.com domain to Client1's Windows 10 machine.</p>
<p><img src="https://i.imgur.com/S55ABgJ.png" height="50%" width="50%" alt="file and text creation"/></p>

<p>To this lab more realistic at the corportate level, let's share this file to a security group. We can do so by navigating to the Server Manager's Active Directory Users and Computers under tools. We will create an Organizational Unit (OU) titled Security Group. In the security group OU we will create a group called Accounting Group. Inside the group properties, we will add ctioukalov, a user in the domain, into the group.</p>        
<p><img src="https://i.imgur.com/Q7CLt8W.png" height="49%" width="49%" alt="security group creation"/>
   <img src="https://i.imgur.com/a1HDID4.png" height="29%" width="29%" alt="adding ctioukalov"/>
</p>

<p>Now, let's right click on the Accounting folder on the desktop and click on properties. We will select on the sharing tab on the top and click on advanced sharing. Now, let's enable sharing to the file and navigate to permissions. We will go ahead and grant the Accounting Group reading permissions to the folder.</p>
<p><img src="https://i.imgur.com/Tiho3MD.png" height="50%" width="50%" alt="properties sharing"/></p>
<p>Note the network path listed in the screenshot above in the Accounting folder properties: \\DCHOMELAB\. We will refer to this later in the lab.</p>

<p>Now, let's see if we are able to access the Accounting folder as ctioukalov, who we just added to the Accounting Group. After logging into ctioukalov, we have to make sure network discovery and file sharing is enabled on Client1's Network tab in file explorer.</p>
<p><img src="https://i.imgur.com/driPeFc.png" height="49%" width="49%" alt="logging into ctioukalov"/>
   <img src="https://i.imgur.com/rE8mugF.png" height="49%" width="49%" alt="network discovery"/>
</p>

<p>Noting the Accounting network file path from earlier, \\DCHOMELAB\, let's search it in the network search bar.</p>
<p><img src="https://i.imgur.com/Vnc0FlE.png" height="50%" width="50%" alt="no permissions"/></p>      
<p>As you can see, we are able to pick up on the folder in network path; however, we need to configure the file permissions correctly.</p>
<p>To enable file permissions, we will have to go back to the domain controller's desktop and navigate to the folder. Towards the top, we will need to select on the share tab, then advanced security. Inside the security settings of the folder, we will have to manually add read permissions to the Accounting Group.</p>
<p><img src="https://i.imgur.com/bU3HKaT.png" height="50%" width="50%" alt="adding permissions"/></p>    

<p>Going back to the Client1 machine, let's see if now have read permissions to access the Accounting folder.</p>
<p><img src="https://i.imgur.com/VPOUs3n.png" height="50%" width="50%" alt="success"/></p>  
<p>YAY! As you can see, we now are able to read the 2023 Accounting .txt file inside the Accounting Folder, which orginiated from another machine in the domain.</p>

<p>Lastly, we should check and see if non-Accounting Group members are denied access to the folder. Now let's log in with Peter Pan's domain credentials.</p>
<p><img src="https://i.imgur.com/2Lbv1de.png" height="50%" width="50%" alt="ppan access attempt"/></p>  
<p>Excellent! Peter Pan does not have the right permissions to read the file. </p><br><br>

<p>Thank you for your time!</p>
