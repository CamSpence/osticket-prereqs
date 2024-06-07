<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Prerequisites and Installation
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />
## Environments and Technologies Used
- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
## Operating Systems Used 
- Windows 10 (21H2)
## List of Prerequisites
- Azure subscription
- new azure resource group
- windows 10 virtual machine
- MySQL 5.5
- PHP 
- osTicket
##  Creating our resources
1. Create a Resource Group
2. Create a Windows 10 Virtual Machine (VM) with 2-4 virtual CPUs
## Installing dependencies

3. Connect to your Virtual Machine with Remote Desktop
4. Install / Enable IIS in Windows by going to the start menu and going to the control panel go to uninstall a program and then click "Turn windows features on or off", check off the following box:
4. Install / Enable IIS in Windows by going to the start menu, control panel, uninstall a program and then click "Turn windows features on or off", check the following box:

![IIs image](./iis.png)

5. Install [Web Platform Installer](./dependecies/WebPlatformInstaller_x64_en-US.msi)
6. Open after installation
7. Search for MySQL 5.5 and add it (*it will ask for credentials to be created later*)
![mysql image](./mysql.png)
  - Name: root
  - Password: Password1
8. Search for PHP and add all simple versions of x86 PHP up until version 7.3
9. Fix any failures if required download from [dependecies folder](./dependecies/) **you can ignore PHP version 5.3.28 if it fails**
<!-- 10. Install [PHP Version 7.3.8](./dependecies/php-7.3.8-Win32-VC15-x86.zip) if it fails -->
11. Install [PHP Manager 1.5.0 for IIS 10](./dependecies/PHPManagerForIIS_V1.5.0.msi) if it fails to install 
12. Install [Microsoft Visual C++ 2009](./dependecies/vcredist_x86.exe) if it fails to install
## Install osTicket v1.15.8
13. Download [osTicket](https://osticket.com/download/)
  - Extract and copy the “upload” folder INTO c:\inetpub\wwwroot
  - Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
@@ -67,27 +67,27 @@
![iis restart](./iis-resart.png)
## Enable Extensions in IIS: Note that some extensions are not enabled
16. Go back to IIS, sites -> Default -> osTicket
17. Double-click PHP Manager
18. Click “Enable or disable an extension”
  - Enable: php_imap.dll
  - Enable: php_intl.dll
  - Enable: php_opcache.dll
![php enable](./enabling-php.png)
## Refresh the osTicket site in your browser, observe the changes
Rename:
  From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

## Assign Permissions: ost-config.php
19. right click the file, go to properties, security, advanced and Disable inheritance -> Remove All
20. Now click add, select a principal, Everyone and give them access to everything, obviously for the sake of practice we're ginving eceryone full control, in a real setup this would be unwise.
20. Now click add, select a principal, "Everyone" and give them access to everything, obviously for the sake of practice we're ginving everyone full control, in a real setup this would be unwise.

![diabling inheritance](./disabling-inheritance.png)

![assinging-new-permissions](./assinging-new-permissions.png)
## Continue Setting up osTicket in the browser (click Continue)
21. Name Helpdesk
22. Default email (receives email from customers)
  - Download and Install [HeidiSQL](https://www.heidisql.com/download.php) 
24. Create a new session, root/Password1
25. Connect to the session
26. Create a database called “osTicket”
## Continue Setting up osticket in the browser
27. MySQL Database: osTicket
28. MySQL Username: root
29. MySQL Password: Password1
  - Click “Install Now!”
