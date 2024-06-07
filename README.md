<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

  - Azure VM running Windows 10
  - <a href="https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view">PHP Manager for IIS v1.5.0</a>
  - <a href="https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view">Rewrite Module</a>
  - <a href="https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view">PHP v7.3.8 NTS</a>
  - <a href="https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view">Microsoft Visual C++ Redistributable</a>
  - <a href="https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view">MySQL v5.5.62</a>
  - <a href="https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe">HeidiSQL v12.3.0.6589</a>

<h2>Installation Steps</h2>

<h3>Create a Resource Group</h3>
  <br>
  <hr>
<h3>Creating A virtual Machine</h3>
<p>
  Next you must create a virtual machine that will host OSticket.
  <img src="https://user-images.githubusercontent.com/142059616/261184714-7833ec95-4dc9-48fa-aa71-b7f4cb8e0e4c.png" height="60%" width="60%" alt="Creating a virtual machine"/>
</p>
</p>
<p>
Let' name our VM "vm-osticket".
</p>
<img src="https://user-images.githubusercontent.com/142059616/261185136-38673ca8-758b-46e2-aa6c-84b84cc58980.png" height="60%" width="60%" alt="Creating a virtual machine"/>
Select the 4vcpu option for the size for optimal performance.
</p>
Create any username and password of your choice. Click "Review + Create". 
</p>
<br />
<hr>

<h3>Connect Virtual Machine using RDP(Remote Desktop)</h3>
<p>
Go to the virtual Machine that was just created and copy the Public IP address. You will find this under the VMs overview page. 
</p>
<p>Open the remote desktop application and paste the IP address. Then you enter your log in information from earlier.
</p>
  <img src="https://user-images.githubusercontent.com/142059616/261189891-ff074ff6-952e-4eb5-b53f-a45ba5e5172a.png" height ="20% "width="50%" alt="Remote Desktop"/>
 <p>You have now successfully created a Virtual Machine!!</p>
<img src="https://user-images.githubusercontent.com/142059616/261193321-14204893-87fb-4a16-b8a3-98555fe5c742.png" height="40%" width="50%"/>


<br />
<hr>
<h3>Enabling Windows Feature</h3>
<img src="https://user-images.githubusercontent.com/142059616/261201802-e22e7d88-ac34-4efc-947c-ade1847aa972.png" height="40%" width="50%"/>
<p>Using the virtual machine press the ⊞ Win key, search for "turn windows features on or off"</p>
<img src="https://user-images.githubusercontent.com/142059616/261413395-56d61bc3-097d-41ba-941c-173c648ba889.png" height="40%" width="50%"/>
<p>- Find "Internet Information Services", then click the checkbox ☐ to enable it 
  - Then, expand the folder by clicking the [+] button next to it.
- Expand "Application Development Features", then checkmark "CGI".
- Expand "Common HTTP Features", then checkmark ALL boxes.
- Click "OK" to apply changes.</p>
<hr>
<br />
<h3>Installing osTicket</h3>
<p>In order for osTicket to run properly, we are going to need to install the prequisite files onto the virtual machine <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Here </p>
<p>Select "download all"</p>
<p>First we will install <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> PHPmanagerForIIS</p>
<p>Next we will install <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">rewrite_amd64_en-US.msi</p>
<p>Next we are going to create a directory</p>
<ul><li>Open Windows C:\ on File Explorer</li>
  create a blank new folder and name it "PHP"</li>
<p>Next, download <a href"https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">php-7.3.8-nts</p>
<p>Right click on the file, select "extract all"->"browse"->find the "PHP" folder-> select "Extract"</p>
<p>Install <a href="https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">VC_redlist.x86.exe</p>
- Next, install <a href="https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view">mysql-5.5.62-win32.msi</a> (MySQL v5.5.62).
- Agree to the License Agreement, then click "Next".
- Click "Typical".
- Once that's complete, click "Finish".
<p align="center">
</p>

- Another window prompt will appear, just click "Next".
- Click "Standard Configuration", then "Next" twice.
- Create a password of your choice for the root login, then click "Next".
- Click "Execute" to start the configuration process.
- Once completed, click "Finish".
<p align="center">
</p>
<hr>

<h3> Register PHP within IIS</h3>

- Press the Windows Key/Button and search for "Internet Information Services (IIS) Manager", then "Run as Administrator".
- Double-click "PHP Manager".
- Under PHP Setup, click on "Register new PHP version".
- Click on the 3-dots "..." to browse for `php-cgi.exe`, located inside the PHP folder on the C:\ drive.
- Once you find it, click "Open" (or double-click the file), then "OK".
<p align="center">
<img src="https://i.imgur.com/ZUbY9fi.jpg" height="20%" width="20%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5vkhmRw.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cvrfkk5.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<hr>

<h3> Installing osTicket: Support Ticketing System</h3>

_Now we are ready to install osTicket!_
- Download <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">osTicket-v1.15.8.zip</a> (osTicket).
  - Open the .zip file (no need to extract all).
- Open another File Explorer window and navigate to **C:\inetpub\wwwroot**.
- Click and Drag the `upload` folder in the .zip file into wwwroot folder (this will automatically extract that specific folder).
- Rename `upload` to `osTicket`.
<p align="center">
<img src="https://i.imgur.com/caVUV5a.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- Return to IIS.
  - On the left sidebar, click "osTicket-VM".
  - Then, on the right sidebar, click "Restart".
<p align="center">
<img src="https://i.imgur.com/RjawCDK.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- On the left sidebar, click the dropdown arrow beside "Sites", same thing with "Default Web Site", then click "osTicket.
  - _The icons in the center window should change._
- On the right sidebar, click "Browse *:80 (http)".
  - This will open a new tab on Microsoft Edge to the osTicket Installer page.
<p align="center">
<img src="https://i.imgur.com/xnYfiBb.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Iyh6UO2.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

_Note that some of the recommended extensions are not enabled, so this will need to be addressed:_
- Return to IIS, still under osTicket folder on the left sidebar, double-click "PHP Manager".
- Under PHP Extensions, click "Enable or disable an extension".
<p align="center">
<img src="https://i.imgur.com/rJNHqxf.jpg" height="30%" width="30%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ao3rSMH.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

- Find the following below, then click "Enable" on the right sidebar:
  - php_imap.dll
  - php_intl.dll
  - php_opcache.dll
- Refresh the osTicket webpage to observe the changes.
  - _APCu Extension & Zend OPcache Extension should be the only two with a Red X._
<p align="center">
<img src="https://i.imgur.com/lJLsKOa.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

- Return to the wwwroot folder in File Explorer.
  - Navagate to **...wwwroot\osTicket\include**.
  - Find `ost-sampleconfig.php`, and Rename it to `ost-config.php` (essentially removing the word sample).
<p align="center">
<img src="https://i.imgur.com/N3FLLaY.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
- Install <a href="https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe">HeidiSQL v12.3.0.6589</a> (Heidi SQL).
<p align="center">
</p>

- In HeidiSQL, click "New" at the bottom left.
- Enter the username **"root"**, and the password you created when installing MySQL.
- Click "Open".
<p align="center">
<img src="https://i.imgur.com/MRTC33j.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

- Right-click "Unnamed" on the left sidebar.
  - Select "Created new" > "Database".
- Type in the name "osTicket", then click "OK".
<p align="center">
<img src="https://i.imgur.com/ULeJErY.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>

- Return the osTicket Installation webpage, click "Continue".
- Under System Settings section:
  - Create a Helpdesk Name of your choice (this example uses **OST Help Desk**).
  - Create a Default Email of your choice (this example uses **ost@helper.com**).
- Under Admin User section, create the appropriate credentials of your choice (example below):
  - **First Name:** ost
  - **Last Name:** user
  - **Email Address:** ostuser@email.com
  - **Username:** ostuser
  - **Password:** Password1
- Under Database Settings section:
  - Enter MySQL Database name that was created in HeidiSLQ (**osTicket**).
  - Enter MySQL Username (default is **root**).
  - Enter MySQL Password (Password you created when installing MySQL).
- Once completed, click "Install Now".
  - _You should then be sent to a Congratulations! page, if no errors._
<p align="center">
<img src="https://i.imgur.com/1GQbv9n.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/sfmeeK5.jpg" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<hr>
