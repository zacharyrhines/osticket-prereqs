<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used</h2>

- Windows 10 (22H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account
- Basic knowledge of IIS
- Remote Desktop access
- osTicket installation files
- HeidiSQL

<h2>Installation Steps</h2>

<h3>1.) Creating a Virtual Machine</h3>

In Microsoft Azure, we will create a VM and add it to a new Resource Group, titled "osTicket". 

- **VM Name:** osticket-vm  
- **Image:** Windows 10 Pro, version 22H2 - x64 Gen2  
- **Size:** 2 vCPUs, 8 GiB memory  

Check the licensing box and review & create the VM. No changes are needed for management, disks, or networking sections.

<p>
<img src="https://imgur.com/tXJV8Nn.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/xIxIeJw.png" height="80%" width="80%" alt="Step 1 Lab 2"/>
</p>

<h3>2.) Accessing the Virtual Machine</h3>

- Log into the VM using **Remote Desktop** with the credentials created during the VM setup.

<p>
<img src="https://imgur.com/qMk46Uw.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>3.) Download and Prepare Installation Files</h3>

- Within the VM, download the `osTicket-Installation-Files.zip` and unzip it to your desktop. The folder should be named `osTicket-Installation-Files`.

<p>
<img src="https://imgur.com/C80xifK.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>4.) Install IIS and Enable Required Features</h3>

- Open **Control Panel** -> **Programs** -> **Turn Windows features on or off**.
- Install/enable **IIS** with the following features:
  - **World Wide Web Services** -> **Application Development Features** -> [X] CGI

<p>
<img src="https://imgur.com/eRYnjkR.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>5.) Install Required Components</h3>

- From the `osTicket-Installation-Files` folder:
  - Install **PHP Manager for IIS**: `PHPManagerForIIS_V1.5.0.msi`.
  - Install **Rewrite Module**: `rewrite_amd64_en-US.msi`.
 
<p>
<img src="https://imgur.com/sBMVZ1D.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>6.) Setup PHP</h3>

- Create the directory `C:\PHP`.
- Unzip `PHP 7.3.8` (`php-7.3.8-nts-Win32-VC15-x86.zip`) into the `C:\PHP` folder.
- Install `VC_redist.x86.exe`.

<p>
<img src="https://imgur.com/aKVDcdX.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/71i0bQq.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>7.) Install MySQL</h3>

- From the `osTicket-Installation-Files` folder, install MySQL 5.5.62 (`mysql-5.5.62-win32.msi`).
  - Select **Typical Setup**.
  - Launch the Configuration Wizard:
    - **Standard Configuration**
    - Input a username and password, don't forget this!

<p>
<img src="https://imgur.com/gU1mmij.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>8.) Configure IIS</h3>

- Open IIS as an administrator.
- Register PHP:
  - Go to **PHP Manager** -> Register PHP path -> `C:\PHP\php-cgi.exe`.
- Reload IIS (Stop and Start the server).

<p>
<img src="https://imgur.com/qGXR04U.png" height="40%" width="50%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/tcm2hns.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/Bpe0NWW.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>


<h3>9.) Install osTicket</h3>

- From the `osTicket-Installation-Files` folder:
  - Unzip `osTicket-v1.15.8.zip`.
  - Copy the `upload` folder into `C:\inetpub\wwwroot`.
  - Rename the `upload` folder to `osTicket`.
- Reload IIS (Stop and Start the server).

<p>
<img src="https://imgur.com/I47ieTi.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/3e1CF2K.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>10.) Configure osTicket</h3>

- Open IIS:
  - Navigate to **Sites** -> **Default** -> **osTicket**.
  - On the right, click **Browse *:80**.

<p>
<img src="https://imgur.com/2BOBiS0.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/A8VD1ZI.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

- Note extensions that are not enabled. Go back to IIS:
  - Navigate to **Sites** -> **Default** -> **osTicket**.
  - Double-click **PHP Manager** -> Click **Enable or disable an extension**.
  - Enable the following extensions:
    - `php_imap.dll`
    - `php_intl.dll`
    - `php_opcache.dll`

<p>
<img src="https://imgur.com/MQLiNUT.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/lpQEvVH.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>11.) Update Configuration Files</h3>

- Rename `ost-config.php`:
  - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
  - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.
- Assign Permissions:
  - Disable inheritance -> Remove all permissions.
  - Add new permissions -> **Everyone** -> **Full control**.

<p>
<img src="https://imgur.com/jiyaAbO.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/DJbCkHg.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/JEZ6DCu.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>12.) Complete osTicket Setup</h3>

- In the browser, continue the osTicket setup:
  - Set **Helpdesk Name**.
  - Set **Default email** (receives emails from customers).

<p>
<img src="https://imgur.com/yEt4fDC.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>13.) Install HeidiSQL and Configure Database</h3>

- From the `osTicket-Installation-Files` folder, install **HeidiSQL**.
- Open HeidiSQL:
  - Create a new session: **Username:** root / **Password:** root.
  - Connect to the session.
  - Create a database named `osTicket`.

<p>
<img src="https://imgur.com/VjjQWVY.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/9Dqt1G7.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>14.) Finalize osTicket Installation</h3>

- In the browser, complete the setup:
  - **MySQL Database:** osTicket  
  - **MySQL Username:** root  
  - **MySQL Password:** root  
- Click **Install Now!**

<p>
<img src="https://imgur.com/h3BQRQB.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>15.) Verify Installation</h3>

- Access your help desk login page: `http://localhost/osTicket/scp/login.php`.

<p>
<img src="https://imgur.com/oHoJDJh.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h2>Conclusion</h2>

Congratulations! You have successfully installed and configured osTicket on your virtual machine. Your help desk system is now ready to use!
</p>

<h2>Conclusion</h2>
