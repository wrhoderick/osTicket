# osTicket Installation Guide

This guide outlines the step-by-step process to install the open-source help desk ticketing system, osTicket. Follow these instructions to set up all the necessary software components for using osTicket in an IT environment.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)
- osTicket (open-source Ticketing System)

## Part 1: Create Virtual Machine in Azure

1. Create a Resource Group.
<img src="https://i.imgur.com/uTEMc4e.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
2. Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs.
<img src="https://i.imgur.com/MlH2uOe.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
4. Allow the VM to create a new Virtual Network (Vnet).

## Part 2: Installation

### Installation Files

Download the necessary files from Google as listed below for osTicket installation.
https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

1.  **Access Your New Virtual Machine Through Remote Desktop and Complete Normal Windows Setup**
2.  **Install / Enable IIS in your Windows Virtual Machine WITH CGI and Common HTTP Features:**
   - Open Control Panel.
   - Navigate to Programs > Programs and Features > "Turn Windows features on and off."

<img src="https://i.imgur.com/oWiwOiq.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

   - Under World Wide Web Services:
      - Application Development Features:
       - [X] CGI
       - [X] Common HTTP Features
       
<img src="https://i.imgur.com/xUS2zkY.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/eDQjRhM.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

3. Install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) and Rewrite Module (rewrite_amd64_en-US.msi).
<img src="https://i.imgur.com/jaGfdKC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

4. Create a directory in C drive: `C:\PHP`.
<img src="https://i.imgur.com/E222253.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

   - Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip its contents into `C:\PHP`.
<img src="https://i.imgur.com/B0zej1i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   - Download and install VC_redist.x86.exe.
<img src="https://i.imgur.com/I9sA5tt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

6. Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
<img src="https://i.imgur.com/XoY3B0S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   - Select Typical Setup.
<img src="https://i.imgur.com/sjgU8XX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   - Launch Configuration Wizard (after install).
<img src="https://i.imgur.com/B0EnwdY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   - Choose Standard Configuration.
<img src="https://i.imgur.com/xD4zLaE.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
   - Set a password, e.g., "Password1."
<img src="https://i.imgur.com/aSEv8Ia.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>

8. Open IIS as an Admin, click on PHP Manager, and register PHP from within IIS.
<img src="https://i.imgur.com/8FPpKEY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Ucn9jPI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/mAgOQfA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

9. Reload IIS (Stop and Start the server).
<img src="https://i.imgur.com/k1aFh9K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

10. **Install osTicket v1.15.8:**
   - Download osTicket, extract, and copy the "upload" folder to `c:\inetpub\wwwroot`.
<img src="https://i.imgur.com/nOw8MbT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   - Rename "upload" to "osTicket."
<img src="https://i.imgur.com/T7afzC2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   - Reload IIS.

11. Enable the following PHP extensions in PHP Manager:
   - php_imap.dll
   - php_intl.dll
   - php_opcache.dll
<img src="https://i.imgur.com/pKhB6ZL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
   - Refresh the osTicket site in your browser.

11. Rename: `ost-config.php` from `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.
<img src="https://i.imgur.com/ouQl2tD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

12. **Assign Permissions to `ost-config.php`:**
    - Right-click on `ost-config.php`.
<img src="https://i.imgur.com/ouQl2tD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

    - Click on Properties > Security tab.
<img src="https://i.imgur.com/l4dPnYY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

    - Disable inheritance.
<img src="https://i.imgur.com/5S7QUbH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/oBJE3In.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
 
    - Add "Everyone" and set Basic permissions to "Read."
<img src="https://i.imgur.com/fQL4zvk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/bphc0S0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 


14. Continue setting up osTicket in the browser:
    - Name: Helpdesk.
    - Default email (receives email from customers).

15. **Download and Install HeidiSQL:**
    - Open HeidiSQL.
    - Create a new session (root/Password1).
    - Connect to the session.
    - Create a database called "osTicket."

16. Continue setting up osTicket in the browser:
    - MySQL Database: osTicket
    - MySQL Username: root
    - MySQL Password: Password1
    - Click "Install Now!"

Congratulations! osTicket should now be installed successfully. Browse to your help desk login page: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php).

End Users osTicket URL: [http://localhost/osTicket/](http://localhost/osTicket/).

## Cleanup

- Delete: `C:\inetpub\wwwroot\osTicket\setup`.
- Set Permissions to "Read" only: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.

## Notes

- Browse to your help desk login page: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php).
- End Users osTicket URL: [http://localhost/osTicket/](http://localhost/osTicket/).
```
