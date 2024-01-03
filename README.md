# osTicket Installation Guide

This guide outlines the step-by-step process to install the open-source help desk ticketing system, osTicket. Follow these instructions to set up all the necessary software components for using osTicket in an IT environment.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)
- osTicket (open-source Ticketing System)

## Part 1: Create Virtual Machine in Azure

1. Create a Resource Group.
2. Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs.
3. Allow the VM to create a new Virtual Network (Vnet).

## Part 2: Installation

### Installation Files

Download the necessary files from Google as listed below for osTicket installation.

1. **Install / Enable IIS in your Windows computer WITH CGI and Common HTTP Features:**
   - Open Control Panel.
   - Navigate to Programs > Programs and Features > "Turn Windows features on and off."
   - Under World Wide Web Services:
     - Application Development Features:
       - [X] CGI
       - [X] Common HTTP Features
     - Internet Information Services:
       - Web Management Tools:
         - [X] IIS Management Console

2. Install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) and Rewrite Module (rewrite_amd64_en-US.msi).

3. Create a directory in C drive: `C:\PHP`.
   - Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip its contents into `C:\PHP`.
   - Download and install VC_redist.x86.exe.

4. Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
   - Select Typical Setup.
   - Launch Configuration Wizard (after install).
   - Choose Standard Configuration.
   - Set a password, e.g., "Password1."

5. Open IIS as an Admin, click on PHP Manager, and register PHP from within IIS.

6. Reload IIS (Stop and Start the server).

7. **Install osTicket v1.15.8:**
   - Download osTicket, extract, and copy the "upload" folder to `c:\inetpub\wwwroot`.
   - Rename "upload" to "osTicket."
   - Reload IIS.

8. Enable the following PHP extensions in PHP Manager:
   - php_imap.dll
   - php_intl.dll
   - php_opcache.dll
   - Refresh the osTicket site in your browser.

9. Rename: `ost-config.php` from `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.

10. **Assign Permissions to `ost-config.php`:**
    - Right-click on `ost-config.php`.
    - Click on Properties > Security tab.
    - Disable inheritance.
    - Add "Everyone" and set Basic permissions to "Read."

11. Continue setting up osTicket in the browser:
    - Name: Helpdesk.
    - Default email (receives email from customers).

12. **Download and Install HeidiSQL:**
    - Open HeidiSQL.
    - Create a new session (root/Password1).
    - Connect to the session.
    - Create a database called "osTicket."

13. Continue setting up osTicket in the browser:
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
