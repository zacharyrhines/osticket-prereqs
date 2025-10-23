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
<img width="80%" height="80%" alt="OSTickPreReqs1" src="https://github.com/user-attachments/assets/38e76e53-76a4-400d-bf44-2f301a88207b"/>
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs2" src="https://github.com/user-attachments/assets/3dc89d23-3d1a-43d3-b8fe-0c345b063252"/>
</p>


<h3>2.) Accessing the Virtual Machine</h3>

- Log into the VM using **Remote Desktop** with the credentials created during the VM setup.

<p>
<img width="80%" height="80%" alt="OSTickPreReqs3" src="https://github.com/user-attachments/assets/30e2682f-a6fa-4fbe-8357-8db7c9f237c0"/>
</p>

<h3>3.) Download and Prepare Installation Files</h3>

- Within the VM, download the `osTicket-Installation-Files.zip` and unzip it to your desktop. The folder should be named `osTicket-Installation-Files`.

<p>
<img width="80%" height="80%" alt="OSTickPreReqs4" src="https://github.com/user-attachments/assets/dd62ab04-98a4-4a01-ae11-d9432440844b"/>
</p>


<h3>4.) Install IIS and Enable Required Features</h3>

- Open **Control Panel** -> **Programs** -> **Turn Windows features on or off**.
- Install/enable **IIS** with the following features:
  - **World Wide Web Services** -> **Application Development Features** -> [X] CGI

<p>
<img width="80%" height="80%" alt="OSTickPreReqs5" src="https://github.com/user-attachments/assets/b1fdb74c-eebb-4e99-88a0-68cd09951e6b"/>
</p>


<h3>5.) Install Required Components</h3>

- From the `osTicket-Installation-Files` folder:
  - Install **PHP Manager for IIS**: `PHPManagerForIIS_V1.5.0.msi`.
  - Install **Rewrite Module**: `rewrite_amd64_en-US.msi`.
 
<p>
<img width="1746" height="778" alt="OSTickPreReqs6" src="https://github.com/user-attachments/assets/df14c45f-1f5a-4217-a8ef-26120982bd70" />

</p>


<h3>6.) Setup PHP</h3>

- Create the directory `C:\PHP`.
- Unzip `PHP 7.3.8` (`php-7.3.8-nts-Win32-VC15-x86.zip`) into the `C:\PHP` folder.
- Install `VC_redist.x86.exe`.

<p>
<img width="80%" height="80%" alt="OSTickPreReqs7" src="https://github.com/user-attachments/assets/42fc1d50-4b80-4b1c-adc6-05ae53b3a7c4" />

</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs8" src="https://github.com/user-attachments/assets/9541bbdb-6105-4f54-bafd-ee3f603f1a63" />

</p>


<h3>7.) Install MySQL</h3>

- From the `osTicket-Installation-Files` folder, install MySQL 5.5.62 (`mysql-5.5.62-win32.msi`).
  - Select **Typical Setup**.
  - Launch the Configuration Wizard:
    - **Standard Configuration**
    - Input a username and password, don't forget this!

<p>
<img width="80%" height="80%" alt="OSTickPreReqs9" src="https://github.com/user-attachments/assets/80ab8964-004d-4e33-9c0e-50d9146e322f" />
</p>


<h3>8.) Configure IIS</h3>

- Open IIS as an administrator.
- Register PHP:
  - Go to **PHP Manager** -> Register PHP path -> `C:\PHP\php-cgi.exe`.
- Reload IIS (Stop and Start the server).

<p>
<img width="50%" height="50%" alt="OSTickPreReqs10" src="https://github.com/user-attachments/assets/bd8b347c-938c-4767-9604-f17aab523645" />
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs11" src="https://github.com/user-attachments/assets/4bda460c-0425-4da9-98a8-37dade11bf89" />
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs12" src="https://github.com/user-attachments/assets/cdd76cf4-2fec-40cc-b051-076d3794eefd" />
</p>


<h3>9.) Install osTicket</h3>

- From the `osTicket-Installation-Files` folder:
  - Unzip `osTicket-v1.15.8.zip`.
  - Copy the `upload` folder into `C:\inetpub\wwwroot`.
  - Rename the `upload` folder to `osTicket`.
- Reload IIS (Stop and Start the server).

<p>
<img width="80%" height="80%" alt="OSTickPreReqs13" src="https://github.com/user-attachments/assets/3a44acd8-9d34-4a74-9750-9295116ec033" />

</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs14" src="https://github.com/user-attachments/assets/1030ff83-a096-4d4c-8b43-e915dae09418" />

</p>


<h3>10.) Configure osTicket</h3>

- Open IIS:
  - Navigate to **Sites** -> **Default** -> **osTicket**.
  - On the right, click **Browse *:80**.

<p>
<img width="80%" height="80%" alt="OSTickPreReqs16" src="https://github.com/user-attachments/assets/ede90798-c577-42e4-a915-808872a570a0"/>
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs17" src="https://github.com/user-attachments/assets/d36e2e7a-9350-43f4-a2a6-d440435c8f5f" />

</p>

- Note extensions that are not enabled. Go back to IIS:
  - Navigate to **Sites** -> **Default** -> **osTicket**.
  - Double-click **PHP Manager** -> Click **Enable or disable an extension**.
  - Enable the following extensions:
    - `php_imap.dll`
    - `php_intl.dll`
    - `php_opcache.dll`

<p>
<img width="80%" height="80%" alt="OSTickPreReqs18" src="https://github.com/user-attachments/assets/7282e3e0-8902-49ef-9101-ea8695af067d" />
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs19" src="https://github.com/user-attachments/assets/6729ab05-faab-4458-aee0-fd9f9c4faae3" />
</p>


<h3>11.) Update Configuration Files</h3>

- Rename `ost-config.php`:
  - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
  - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.
- Assign Permissions:
  - Disable inheritance -> Remove all permissions.
  - Add new permissions -> **Everyone** -> **Full control**.

<p>
<img width="80%" height="80%" alt="OSTickPreReqs20" src="https://github.com/user-attachments/assets/4ff2fed2-cf57-4fc6-96ce-3fa3893fd988" />
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs21" src="https://github.com/user-attachments/assets/ab522f27-c34b-46c6-8516-2b0981b1cce6" />
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs22" src="https://github.com/user-attachments/assets/dd50087e-77ce-4375-9673-39ef8b2e4eb0" />
</p>

<h3>12.) Complete osTicket Setup</h3>

- In the browser, continue the osTicket setup:
  - Set **Helpdesk Name**.
  - Set **Default email** (receives emails from customers).

<p>
<img width="80%" height="80%" alt="OSTickPreReqs23" src="https://github.com/user-attachments/assets/bc8c3ac4-ff39-4935-b740-a6371a263bc5" />

</p>


<h3>13.) Install HeidiSQL and Configure Database</h3>

- From the `osTicket-Installation-Files` folder, install **HeidiSQL**.
- Open HeidiSQL:
  - Create a new session: **Username:** root / **Password:** root.
  - Connect to the session.
  - Create a database named `osTicket`.

<p>
<img width="80%" height="80%" alt="OSTickPreReqs24" src="https://github.com/user-attachments/assets/b84f4463-717f-47fc-a5e5-747227e36063" />
</p>

<p>
<img width="80%" height="80%" alt="OSTickPreReqs25" src="https://github.com/user-attachments/assets/e6e63460-04ce-4ae3-901d-4799c20eadcc" />

</p>


<h3>14.) Finalize osTicket Installation</h3>

- In the browser, complete the setup:
  - **MySQL Database:** osTicket  
  - **MySQL Username:** root  
  - **MySQL Password:** root  
- Click **Install Now!**

<p>
<img width="80%" height="80%" alt="OSTickPreReqs26" src="https://github.com/user-attachments/assets/668f09ad-d6c7-45ce-99c4-c6ec3b92406c" />

</p>


<h3>15.) Verify Installation</h3>

- Access your help desk login page: `http://localhost/osTicket/scp/login.php`.

<p>
<img width="80%" height="80%" alt="OSTickPreReqs27" src="https://github.com/user-attachments/assets/24340609-0583-4c9d-a167-fbd6392cbe14" />

</p>

<h2>Conclusion</h2>

Congratulations! You have successfully installed and configured osTicket on your virtual machine. Your help desk system is now ready to use!
</p>
