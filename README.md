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
- **PHP 7.4 & PHP Manager** (Server-Side Script Processing)
- **MySQL Database & HeidiSQL** (Backend Data Management)
- **Web Browser** (Chrome / Edge)

<h2>Languages Used</h2>

- **PHP** (Core Application Code)
- **SQL** (Database Creation and Queries)

<h2>Operating Systems Used</h2>

- **Windows 10 / 11 Pro** (Azure Virtual Machine Web Host)

<h2>List of Prerequisites</h2>

- **Microsoft Azure Subscription:** Active account to host the virtual server environment.
- **Windows Virtual Machine:** Deployed as the primary workstation and web host.
- **IIS (Internet Information Services):** Enabled with CGI features to host web applications.
- **PHP 7.4 & MySQL Engine:** Essential for processing PHP scripts and storing application tables.
- **osTicket Core Files:** Extracted and configured within the web server directory (`C:\inetpub\wwwroot`).

<br />

---

<h2>Installation & Setup Steps</h2>

<h2>Step 1: Setting Up the Virtual Workspace</h2>

Before installing web software, you need a dedicated server host environment. In Microsoft Azure, I provisioned a Windows Virtual Machine to serve as the isolated web server for hosting the help desk platform.

1. Logged into the Azure Portal and navigated to **Virtual Machines**.
2. Created a new virtual machine using a Windows client image.
3. Connected to the instance using **Remote Desktop Connection (RDP)** to begin server configuration.

<p align="center">
<img width="1192" height="476" alt="Step 1 - Setting up Virtual Workspace" src="https://github.com/user-attachments/assets/1771b82f-edb9-4613-bb19-61e5321b2d88" />
</p>

<br />

---

<h2>Step 2: Preparing the Web Server (IIS)</h2>

Windows operating systems do not act as web servers by default. I enabled **Internet Information Services (IIS)** along with the **CGI (Common Gateway Interface)** module through Windows Features so the machine could host web applications.

1. Opened **Control Panel** -> **Programs and Features** -> **Turn Windows features on or off**.
2. Expanded **Internet Information Services** -> **World Wide Web Services** -> **Application Development Features**.
3. Checked **CGI**, clicked **OK**, and allowed Windows to install the required web hosting components.

<p align="center">
<img width="647" height="493" alt="Step 2 - Enabling IIS and CGI" src="https://github.com/user-attachments/assets/4b008e5f-5591-4361-aee3-465137420484" />
</p>

<br />

---

<h2>Step 3: Installing & Registering PHP</h2>

The osTicket core application is written in **PHP**. Since Windows IIS does not process PHP out of the box, I installed PHP 7.4 and used **PHP Manager for IIS** to register the interpreter path with the web server.

1. Extracted PHP 7.4 files into `C:\PHP`.
2. Installed PHP Manager for IIS.
3. Opened **IIS Manager**, launched **PHP Manager**, and selected **Register new PHP version**.
4. Pointed the registration tool directly to `C:\PHP\php-cgi.exe` and enabled required PHP extensions (such as `php_mysqli.dll` and `php_mbstring.dll`).

<p align="center">
<img width="951" height="510" alt="Step 3 - Registering PHP in IIS" src="https://github.com/user-attachments/assets/d9c3ee16-3b5d-4db7-8500-6e9c2b7b36c4" />
</p>

<br />

---

<h2>Step 4: Building the Backend Database (MySQL & HeidiSQL)</h2>

Every help desk requires a relational database to store user records, department structures, and ticket history. I installed MySQL Server and used **HeidiSQL** to connect to the local database instance and create a blank target database named `osticket`.

1. Installed MySQL Database Server on the local machine.
2. Opened **HeidiSQL** and logged in using local root database credentials.
3. Created a new database named **`osticket`** to serve as the backend storage container for the web installer.

<p align="center">
<img width="980" height="598" alt="Step 4 - Creating Database in HeidiSQL" src="https://github.com/user-attachments/assets/445a572f-782c-41a7-b1e7-136735e64e7f" />
</p>

<br />

---

<h2>Step 5: Final Web Installation & Success Verification</h2>

With the web server configured, PHP interpreter linked, and MySQL database provisioned, I initiated the osTicket web-based installer wizard.

1. Placed the osTicket `upload` directory files into `C:\inetpub\wwwroot\osTicket`.
2. Opened a web browser and navigated to `http://localhost/osTicket/setup`.
3. Completed the system prerequisites check, provided admin account details, and linked the database credentials created in Step 4.
4. Completed the installer and landed on the official confirmation screen, confirming the help desk system was live and ready for deployment.

<p align="center">
<img width="1110" height="598" alt="Step 5 - Installation Complete Screen" src="https://github.com/user-attachments/assets/38617844-3423-422d-8c7b-501aec1c7fbe" />
</p>
