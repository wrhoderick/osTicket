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
   - Select Typical Setup.
   - Launch Configuration Wizard (after install).
   - Choose Standard Configuration.
   - Set a password, e.g., "Password1."

7. Open IIS as an Admin, click on PHP Manager, and register PHP from within IIS.

8. Reload IIS (Stop and Start the server).

9. **Install osTicket v1.15.8:**
   - Download osTicket, extract, and copy the "upload" folder to `c:\inetpub\wwwroot`.
   - Rename "upload" to "osTicket."
   - Reload IIS.

10. Enable the following PHP extensions in PHP Manager:
   - php_imap.dll
   - php_intl.dll
   - php_opcache.dll
   - Refresh the osTicket site in your browser.

11. Rename: `ost-config.php` from `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.

12. **Assign Permissions to `ost-config.php`:**
    - Right-click on `ost-config.php`.
    - Click on Properties > Security tab.
    - Disable inheritance.
    - Add "Everyone" and set Basic permissions to "Read."

13. Continue setting up osTicket in the browser:
    - Name: Helpdesk.
    - Default email (receives email from customers).

14. **Download and Install HeidiSQL:**
    - Open HeidiSQL.
    - Create a new session (root/Password1).
    - Connect to the session.
    - Create a database called "osTicket."

15. Continue setting up osTicket in the browser:
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
