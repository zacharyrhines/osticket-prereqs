<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account
- Basic knowledge of IIS
- Remote Desktop access
- osTicket installation files
- HeidiSQL

<h2>Installation Steps</h2>

<p>
In Microsoft Azure, we will create a VM and add it to a new Resource Group, titled "osTicket". 

- **VM Name:** osticket-vm  
- **Image:** Windows 10 Pro, version 22H2 - x64 Gen2  
- **Size:** 2 vCPUs, 8 GiB memory  

Check the licensing box and review & create the VM. No changes are needed for management, disks, or networking sections.

<p>
<img src="https://i.imgur.com/Bz829jL.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/tXJV8Nn.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>2.) Accessing the Virtual Machine</h3>

- Log into the VM using **Remote Desktop** with the credentials created during the VM setup.

<p>
<img src="https://i.imgur.com/8IdvRmZ.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/qMk46Uw.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>3.) Download and Prepare Installation Files</h3>

- Within the VM, download the `osTicket-Installation-Files.zip` and unzip it to your desktop. The folder should be named `osTicket-Installation-Files`.

<p>
<img src="https://i.imgur.com/6imV7Hy.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/C80xifK.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>4.) Install IIS and Enable Required Features</h3>
@@ -66,15 +66,7 @@
  - **World Wide Web Services** -> **Application Development Features** -> [X] CGI

<p>
<img src="https://i.imgur.com/Htr4j9h.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/4Q1PaOl.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/cm20H8J.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/eRYnjkR.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>5.) Install Required Components</h3>
@@ -84,7 +76,7 @@
  - Install **Rewrite Module**: `rewrite_amd64_en-US.msi`.

<p>
<img src="https://i.imgur.com/TmRwTh9.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/sBMVZ1D.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>6.) Setup PHP</h3>
@@ -94,11 +86,11 @@
- Install `VC_redist.x86.exe`.

<p>
<img src="https://i.imgur.com/Khwf0Tv.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/aKVDcdX.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/0IRX6FM.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/71i0bQq.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>7.) Install MySQL</h3>
@@ -110,7 +102,7 @@
    - Input a username and password, don't forget this!

<p>
<img src="https://i.imgur.com/m5NO1HX.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/gU1mmij.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>8.) Configure IIS</h3>
@@ -121,13 +113,18 @@
- Reload IIS (Stop and Start the server).

<p>
<img src="https://i.imgur.com/m5NO1HX.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/qGXR04U.png" height="40%" width="50%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/tcm2hns.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/OPR6ELG.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/Bpe0NWW.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>


<h3>9.) Install osTicket</h3>

- From the `osTicket-Installation-Files` folder:
@@ -137,11 +134,11 @@
- Reload IIS (Stop and Start the server).

<p>
<img src="https://i.imgur.com/QAGjmly.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/I47ieTi.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/UNeiP4j.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/3e1CF2K.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>10.) Configure osTicket</h3>
@@ -151,11 +148,11 @@
  - On the right, click **Browse *:80**.

<p>
<img src="https://i.imgur.com/Vo85YbB.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/2BOBiS0.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/oM0muFz.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/A8VD1ZI.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

- Note extensions that are not enabled. Go back to IIS:
@@ -167,7 +164,11 @@
    - `php_opcache.dll`

<p>
<img src="https://i.imgur.com/3w4E5N7.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/MQLiNUT.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/lpQEvVH.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>11.) Update Configuration Files</h3>
@@ -180,11 +181,15 @@
  - Add new permissions -> **Everyone** -> **Full control**.

<p>
<img src="https://i.imgur.com/18W6jYt.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/jiyaAbO.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://imgur.com/DJbCkHg.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/Gj686F9.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/JEZ6DCu.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>12.) Complete osTicket Setup</h3>
@@ -194,7 +199,7 @@
  - Set **Default email** (receives emails from customers).

<p>
<img src="https://i.imgur.com/lFfXfPa.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/yEt4fDC.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>13.) Install HeidiSQL and Configure Database</h3>
@@ -206,11 +211,11 @@
  - Create a database named `osTicket`.

<p>
<img src="https://i.imgur.com/3MktR5j.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/VjjQWVY.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<p>
<img src="https://i.imgur.com/45BnPbc.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/9Dqt1G7.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>14.) Finalize osTicket Installation</h3>
@@ -222,15 +227,15 @@
- Click **Install Now!**

<p>
<img src="https://i.imgur.com/niqOpoY.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/h3BQRQB.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h3>15.) Verify Installation</h3>

- Access your help desk login page: `http://localhost/osTicket/scp/login.php`.

<p>
<img src="https://i.imgur.com/fsadUTz.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
<img src="https://imgur.com/oHoJDJh.png" height="80%" width="80%" alt="Step 1 Lab 3"/>
</p>

<h2>Conclusion</h2>
