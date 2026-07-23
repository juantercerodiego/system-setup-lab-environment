<p align="center">
<img width="500" src="https://sjredwings-cdn.fxbrt.com/downloads/icons/os_ticket_sj_logo.png" alt="osTicket Logo"/>
</p>

<h1>osTicket - System Setup & Lab Environment Deployment</h1>

**Quick Note:** This guide provides a complete, step-by-step walkthrough of deploying and configuring an osTicket server environment in Microsoft Azure. Once this server setup is complete, you can view the second phase—where I simulate day-to-day help desk operations and ticket lifecycles—here: [Link to your osTicket Ticket Lifecycle README].

This lab covers setting up the underlying web infrastructure, enabling web server features, installing script interpreters, provisioning backend databases, and running the final application installer.

<h2>Environments and Technologies Used</h2>

- **Microsoft Azure** (Virtual Machine Server Host)
- **Remote Desktop Connection (RDP)** (Remote Server Administration)
- **Internet Information Services (IIS)** (Windows Web Server)
- **PHP 7.3.8 & PHP Manager** (Server-Side Script Processing)
- **MySQL Database 5.5.62 & HeidiSQL** (Backend Data Management)
- **Web Browser** (Chrome / Edge)

<h2>Languages Used</h2>

- **PHP** (Core Application Code)
- **SQL** (Database Creation and Queries)

<h2>Operating Systems Used</h2>

- **Windows 10 / 11 Pro** (Azure Virtual Machine Web Host)

<h2>List of Prerequisites</h2>

- **Microsoft Azure Subscription:** Active account to host the virtual server environment.
- **Windows Virtual Machine:** Deployed as the primary workstation and web host (`osticket-vm`).
- **IIS (Internet Information Services):** Enabled with CGI features to host web applications.
- **PHP 7.3.8 & MySQL Engine 5.5.62:** Essential for processing PHP scripts and storing application tables.
- **osTicket Core Files (v1.15.8):** Extracted and configured within the web server directory (`C:\inetpub\wwwroot\osTicket`).

<br />

---

<h2>Installation & Setup Steps</h2>

<h2>Step 1: Setting Up the Virtual Workspace</h2>

Before installing web software, you need a dedicated server host environment. In Microsoft Azure, I logged into the target virtual machine (`osticket-vm`) via Remote Desktop and prepared the installation media.

1. Logged into the **`osticket-vm`** using **Remote Desktop Connection (RDP)**.
2. Downloaded `osTicket-Installation-Files.zip` and unzipped it directly onto the Desktop.
3. Opened the `osTicket-Installation-Files` directory containing all core installation packages and dependency installers.

<img width="1192" height="476" alt="step 1 osticket" src="https://github.com/user-attachments/assets/23b7e5ea-3e0c-443d-a6d3-68d153004bcb" />


<br />

---

<h2>Step 2: Preparing the Web Server (IIS)</h2>

Windows operating systems do not act as web servers by default. I enabled **Internet Information Services (IIS)** along with the **CGI (Common Gateway Interface)** module through Windows Features so the machine could host web applications.

1. Opened **Control Panel** -> **Programs and Features** -> **Turn Windows features on or off**.
2. Expanded **Internet Information Services** -> **World Wide Web Services** -> **Application Development Features**.
3. Checked **CGI**, clicked **OK**, and allowed Windows to install the required web hosting components.

<img width="647" height="714" alt="step 2" src="https://github.com/user-attachments/assets/1d5cdccf-6a9a-486e-b101-23018a9a6f82" />


<br />

---

<h2>Step 3: Installing Prerequisites & Registering PHP</h2>

The osTicket core application is written in **PHP**. Since Windows IIS does not process PHP out of the box, I installed the required IIS modules, deployed PHP 7.3.8, and registered the interpreter with IIS.

1. From the `osTicket-Installation-Files` folder, installed **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`) and the **URL Rewrite Module** (`rewrite_amd64_en-US.msi`).
2. Created directory `C:\PHP` and unzipped **PHP 7.3.8** (`php-7.3.8-nts-Win32-VC15-x86.zip`) directly into `C:\PHP`.
3. Installed `VC_redist.x86.exe` from the installation folder.
4. Opened **IIS Manager** as Administrator, opened **PHP Manager**, registered `C:\PHP\php-cgi.exe`, and restarted the IIS web server.
5. In **PHP Manager**, clicked **Enable or disable an extension** and enabled:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`

<img width="951" height="617" alt="step 3" src="https://github.com/user-attachments/assets/adb15174-e828-402b-b09f-549d6e22b758" />


<br />

---

<h2>Step 4: Building the Backend Database (MySQL & HeidiSQL)</h2>

Every help desk requires a relational database to store user records, department structures, and ticket history. I installed MySQL Server 5.5.62 and used **HeidiSQL** to create a blank database named `osTicket`.

1. Installed **MySQL 5.5.62** (`mysql-5.5.62-win32.msi`) using a Typical Setup.
2. Launched the MySQL Configuration Wizard, selected **Standard Configuration**, and set the root admin account password (`root`).
3. Installed and opened **HeidiSQL**, created a new session connecting to localhost with username `root` and password `root`.
4. Created a brand new database named **`osTicket`**.

<img width="980" height="598" alt="step4" src="https://github.com/user-attachments/assets/de281375-1418-4ff0-9155-2795524dd5e5" />


<br />

---

<h2>Step 5: Deploying osTicket, Web Setup & Security Cleanup</h2>

With the web server configured, PHP interpreter linked, and MySQL database provisioned, I deployed **osTicket v1.15.8**, adjusted file permissions, and completed the web installer wizard.

1. Unzipped `osTicket-v1.15.8.zip`, copied the `upload` folder into `C:\inetpub\wwwroot`, and renamed `upload` to **`osTicket`**.
2. Renamed `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `ost-config.php`.
3. Configured security permissions on `ost-config.php` (Disabled inheritance, removed existing permissions, assigned `Everyone` -> `Full Control`).
4. Opened browser, navigated to `http://localhost/osTicket/setup`, and linked the database (`osTicket`, user: `root`, pass: `root`).
5. **Post-Installation Cleanup:** Deleted the installation setup folder (`C:\inetpub\wwwroot\osTicket\setup`) and reset permissions on `ost-config.php` back to **Read-Only**.
6. Verified system deployment by accessing the end-user portal (`http://localhost/osTicket/`) and staff portal (`http://localhost/osTicket/scp/login.php`).

<img width="1110" height="909" alt="step 5" src="https://github.com/user-attachments/assets/7736a6e7-f226-4f56-9dda-da3d88d2dc12" />

