# Setting Up a Help Desk Ticketing System with osTicket

## Description
This project guides you through setting up osTicket, an open-source help desk ticketing system, on a local web server using a Windows 10 Pro virtual machine. You'll learn how to configure Internet Information Services (IIS), install necessary components like PHP and MySQL, and set up osTicket for use in a simulated help desk environment.

## Languages and Utilities Used
- HTML
- PHP
- MySQL
- Windows PowerShell

## Environments Used
- Windows 10 Pro (22H2)
- Oracle VirtualBox
- Internet Information Services (IIS)

## Program Walk-through

### 1. Set Up Virtual Machine
1. Download and install Oracle VirtualBox
2. Download Windows 10 Pro ISO
3. In VirtualBox, click "New" to create a new VM
4. Name the VM "osTicket" and select the Windows 10 Pro ISO
5. Allocate 8GB RAM and 4 CPUs
6. Create a 50GB virtual hard drive
7. Start the VM and complete Windows 10 Pro installation

### 2. Configure VM Display
1. Go to "Devices" in VirtualBox menu
2. Select "Insert Guest Additions CD image"
3. In the VM, open File Explorer and run VBoxWindowsAdditions-amd64
4. Follow installation prompts and restart VM

### 3. Enable Internet Information Services (IIS)
1. Open Control Panel
2. Navigate to Programs > Turn Windows features on or off
3. Enable the following:
   - Internet Information Services
   - World Wide Web Services > Common HTTP Features (all)
   - World Wide Web Services > Application Development Features > CGI
   - Internet Information Services > Web Management Tools > IIS Management Console
4. Click OK and wait for installation to complete
5. Test IIS by opening a web browser and navigating to 127.0.0.1

### 4. Install PHP Manager for IIS
1. Search for "PHP Manager for IIS" in your web browser
2. Download and install the latest version

### 5. Install Rewrite Module
1. Search for "URL Rewrite Module" in your web browser
2. Download and install the x64 version

### 6. Create PHP Directory
1. Open File Explorer
2. Navigate to C: drive
3. Create a new folder named "PHP"

### 7. Install PHP
1. Search for "PHP for Windows" in your web browser
2. Download the latest Non-Thread Safe ZIP package
3. Extract contents to C:\PHP

### 8. Install MySQL
1. Search for "MySQL Installer" in your web browser
2. Download the latest version
3. Run installer, selecting "Server only" option
4. Follow installation prompts, using a simple password for this lab environment

### 9. Register PHP with IIS
1. Open IIS Manager as administrator
2. Click on "PHP Manager"
3. Choose "Register new PHP version"
4. Browse to C:\PHP\php-cgi.exe
5. Select the file and click "Open"
6. Restart the IIS server

### 10. Install osTicket
1. Download latest osTicket from official website
2. Extract "upload" folder to C:\inetpub\wwwroot
3. Rename "upload" folder to "osTicket"

### 11. Configure osTicket in IIS
1. In IIS Manager, go to Sites > Default Web Site > osTicket
2. Click "Browse *:80" to open osTicket in browser
3. Note any missing extensions

### 12. Enable PHP Extensions
1. In IIS Manager, double-click "PHP Manager"
2. Click "Enable or disable an extension"
3. Enable: php_imap.dll, php_intl.dll, php_opcache.dll

### 13. Rename ost-config.php
1. Navigate to C:\inetpub\wwwroot\osTicket\include\
2. Rename ost-sampleconfig.php to ost-config.php

### 14. Set Permissions for ost-config.php
1. Right-click ost-config.php, select Properties
2. Go to Security tab > Advanced
3. Disable inheritance and remove all permissions
4. Add new permission for Everyone with Full control

### 15. Continue osTicket Setup in Browser
1. Refresh osTicket page in browser
2. Fill in Helpdesk Name and Default Email
3. Create Admin User account

### 16. Install HeidiSQL
1. Download HeidiSQL from official website
2. Install with default options

### 17. Set Up Database for osTicket
1. Open HeidiSQL
2. Create a new session (user: root, password: your MySQL password)
3. Connect to the session
4. Create a new database named "osTicket"

### 18. Complete osTicket Installation
1. Return to osTicket browser setup
2. Enter database information:
   - MySQL Database: osTicket
   - MySQL Username: root
   - MySQL Password: (your password)
3. Click "Install Now"

### 19. Clean Up
1. Delete C:\inetpub\wwwroot\osTicket\setup directory
2. Set ost-config.php permissions to "Read" only

### 20. Access osTicket
- Staff Control Panel: http://localhost/osTicket/scp/login.php
- Customer Portal: http://localhost/osTicket/
