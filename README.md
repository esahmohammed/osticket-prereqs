<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

<h2>Installation Steps</h2>

<p>
Welcome to my tutorial on how to install OsTicket. For our first step, you want to go and create a Windows 10 Virtual Machine using Microsoft Azure. We're using a virtual machine to make sure that we protect our own machine incase any problems arise. To start create a resource group and a virtual machine of Windows 10 that uses the resource group that we just created.
</p>
<br />

<p>
<img src="https://i.imgur.com/7YEkwr5.png" height="40%" width="40%" alt="Virtual Machine"/>
</p>
<p>
Okay great! Now we’ll connect to our virtual machine (vn) using its public IPv4 Address in Microsoft Remote Desktop (RDP) if you are on Mac you can do so by downloading Microsoft Remote Desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/4EL26QY.png" height="40%" width="40%" alt="IPv4 Address"/>
</p>

<p>
<img src="https://i.imgur.com/iMdkZKX.png" height="40%" width="40%" alt="RDP"/>
</p>

<p>
Once you are connected to your VM you must enable IIS. To do so, we’ll go to our control panel using our windows start menu and typing in “control panel” from here select “uninstall a program” then “turn windows features on or off”. Enable Internet Information Systems >> World Wide Web Services >> Application Development Features >> CGI box
</p>
<br />

<p>
<img src="https://i.imgur.com/3nSoMaN.png" height="40%" width="40%" alt="IIS Installation"/>
</p>

<p>
Next download and install the following files, PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) and Rewrite Module (rewrite_amd64_en-US.msi)
</p>

<p>
<img src="https://i.imgur.com/zpHMKmx.png" height="40%" width="40%" alt="PHP Manager for IIS"/>
</p>

<p>
<img src="https://i.imgur.com/VvMMFQQ.png" height="40%" width="40%" alt="Rewrite Module for IIS"/>
</p>

<p>
Afterwards we will create the directory C:\PHP by going into our local disk and creating a folder called “PHP”.
</p>

<p>
<img src="https://i.imgur.com/JZaQr4e.png" height="40%" width="40%" alt="PHP Folder"/>
</p>

<p>
Once you have done this step we can download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
</p>

<p>
<img src="https://i.imgur.com/daigPlY.png" height="40%" width="40%" alt="PHP Directory"/>
</p>

<p>
Next we download download and install VC_redist.x86.exe, then download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
</p>

<p>
<img src="https://i.imgur.com/XuI55Oz.png" height="40%" width="40%" alt="VC_redist"/>
</p>

<p>
<img src="https://i.imgur.com/FmehH94.png" height="40%" width="40%" alt="MySQL"/>
</p>

<p>
Follow these steps when installing MySQL 5.5.62
Step 1: Typical Setup
<p>
<img src="https://i.imgur.com/KiqaVvC.png" height="40%" width="40%" alt="Typical"/>
</p>
Step 2: Launch Configuration Wizard after installation <br />
Step 3: Standard Configuration
<p>
<img src="https://i.imgur.com/MEHvsn0.png" height="40%" width="40%" alt="Standard Configuration"/>
</p>
Step 4: Password1
<p>
<img src="https://i.imgur.com/QGuUrms.png" height="40%" width="40%" alt="root/password"/>
</p>

<p>
Note that the User is “root” and the password can be anything you want it to be as long as you remember it because this is crucial for the future steps.
</p>
<br />

<p>
Next we will open IIS as an Admin and register PHP from within IIS by double clicking on “PHP Manager” and selecting “Register new PHP Version”.
</p>
<p>
<img src="https://i.imgur.com/03mt472.png" height="40%" width="40%" alt="IIS Admin"/>
</p>

<p>
<img src="https://i.imgur.com/eNhSSxt.png" height="40%" width="40%" alt="PHP Manager"/>
</p>

<p>
<img src="https://i.imgur.com/efhUGST.png" height="40%" width="40%" alt="Register new PHP version"/>
</p>

<p>
From here we go to C:\PHP and select php-cgi, then open. 
</p>
<p>
<img src="https://i.imgur.com/PGuslyF.png" height="40%" width="40%" alt="New PHP Version"/>
</p>
<p>
Great! We have now registered a new PHP version. Now we reload IIS by opening IIS, clicking stop and start.
</p>

<p>
<img src="https://i.imgur.com/YsgehzX.png" height="40%" width="40%" alt="stop start IIS"/>
</p>

<p>
Okay now we can download osTicket. Once downloaded extract the zip file and copy the upload folder to the following path: c:\inetpub\wwwroot
After doing so, rename the upload folder to osTicket 
</p>
<p>
<img src="https://i.imgur.com/2tjVKHv.png" height="40%" width="40%" alt="osTicket"/>
</p>

<p>
For our next step we will open IIS Manager and restart the server by selecting stop and then start. In IIS Manager select the following: Sites >> Default >> osTicket then click on “Browse*.80” which should be located to the right. The osTicket web server should now open on your browser.
</p>
<p>
<img src="https://i.imgur.com/59qz1Z9.png" height="40%" width="40%" alt="Browse 80"/>
</p>

<p>
In order for us to continue we first need to enable 3 extensions. To do so we will go back to IIS Manager, select Sites >> Default >> osTicket then enter PHP Manager, select “Enable or Disable an extension” and enable the following: <br />
Enable: php_imap.dll <br />
Enable: php_intl.dll<br />
Enable: php_opcache.dll<br />
</p>
<p>
<img src="https://i.imgur.com/n7eWR8X.png" height="40%" width="40%" alt="Enable or disable an extension"/>
</p>

<p>
<img src="https://i.imgur.com/cbnuiG6.png" height="40%" width="40%" alt="dll files"/>
</p>

<p>
Refreshing osTicket in our browser, we should now see the following changes.
</p>

<p>
<img src="https://i.imgur.com/S4f7zSx.png" height="40%" width="40%" alt="osTicket Changes"/>
</p>

<p>
Before we continue we need to rename a file from: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<br />

We rename the ost-sampleconfig.php to ost-config.php
</p>
<p>
<img src="https://i.imgur.com/VfFJISk.png" height="40%" width="40%" alt="Rename ost 1"/>
</p>
<p>
<img src="https://i.imgur.com/FUWTlgu.png" height="40%" width="40%" alt="Rename ost 2"/>
</p>

<p>
Next we will be assigning permissions to “ost-config.php”. Begin by right clicking ost-config.php and selecting properties. After, select Security >> Advanced >> Disable Inheritance and click on remove all permissions.
</p>

<p>
<img src="https://i.imgur.com/IKiF5NC.png" height="40%" width="40%" alt="Disable Inheritance"/>
</p>
<p>
<img src="https://i.imgur.com/C8Z8q4u.png" height="40%" width="40%" alt="Remove all permissions"/>
</p>

<p>
Now we will click on Add >> Select a principal, type “everyone”, click “Check Names” and click Ok. Give everyone full permissions now that we are able to do so.
</p>
<p>
<img src="https://i.imgur.com/Kyh5Wzi.png" height="40%" width="40%" alt="Click Add"/>
</p>
<p>
<img src="https://i.imgur.com/8HQOBzL.png" height="40%" width="40%" alt="Select Principal"/>
</p>
<p>
<img src="https://i.imgur.com/vg9WJlX.png" height="40%" width="40%" alt="Everyone"/>
</p>

<p>
Give everyone full permissions now that we are able to do so.
</p>
<p>
<img src="https://i.imgur.com/cUFACp5.png" height="40%" width="40%" alt="Permissions"/>
</p>

<p>
Afterward we can continue to setup osTicket in our web browser by clicking continue. Enter the credentials correspondingly, and use a default email to ensure you receive emails from customers who send tickets.
</p>
<p>
<img src="https://i.imgur.com/ovus0RT.png" height="40%" width="40%" alt="osTicket Setup"/>
</p>

<p>
Before we fill out our last 3 credentials we need to download and install HeidiSQL. Once installed, open HeidiSQL and create a new session. Begin by clicking new, in User type “root” and in Password: “Password1”, then click on open to connect to the session.
</p>
<p>
<img src="https://i.imgur.com/J4Noc0x.png" height="40%" width="40%" alt="Installing HeidiSQL"/>
</p>
<p>
<img src="https://i.imgur.com/xpJ74e9.png" height="40%" width="40%" alt="Creating Heidi new session"/>
</p>

<p>
In the session create a database called “osTicket” by right clicking on unnamed and selecting Create New >> Database. Name the database osTicket and click OK.
</p>

<p>
<img src="https://i.imgur.com/7NMuHPC.png" height="40%" width="40%" alt="Creating a new Database in Heidi"/>
</p>

<p>
<img src="https://i.imgur.com/ngfTZql.png" height="40%" width="40%" alt="Naming the Database"/>
</p>

<p>
Now we can go back to our browser and fill out the remaining credentials on the osTicket web server<br />
Enter the following:<br />
MySQL Database: osTicket<br />
MySQL Username: root<br />
MySQL Password: Password1<br />
After doing so click install.<br />
<br />

<p>
<img src="https://i.imgur.com/4UagEjY.png" height="40%" width="40%" alt="Database credentials"/>
</p>

Congratulations 🎉 if you followed each step correctly osTicket should now be installed with no errors!
<p>
<img src="https://i.imgur.com/0xIFv22.png" height="40%" width="40%" alt="osTicket Successfuly Setup"/>
</p>

<p>
The last thing we will be doing for this tutorial is some clean up. Go to the following path: C:\inetpub\wwwroot\osTicket\setup and delete only the “setup” folder. Next set “ost-config.php”permissions to “Read” only in C:\inetpub\wwwroot\osTicket\include\ost-config.php 
</p>
<p>
<img src="https://i.imgur.com/SB4jLIH.png" height="40%" width="40%" alt="Deleting Setup"/>
</p>
<p>
<img src="https://i.imgur.com/Oojxc6w.png" height="40%" width="40%" alt="Setting permissions to read only"/>
</p>


