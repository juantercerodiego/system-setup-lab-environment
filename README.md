<p align="center">
<img src="https://sjredwings-cdn.fxbrt.com/downloads/icons/os_ticket_sj_logo.png"/>
</p>

<h1>osTicket - System Setup & Lab Environment</h1>
This guide provides a step-by-step walkthrough of deploying osTicket, covering everything from environment prerequisites to final server installation..<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop (RDP)
- Internet Information Services (IIS)
- MySQL & PHP Manager

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- **Microsoft Azure Subscription**: Used to host the virtual server environment.
- **Windows 10 VM**: Deployed as the primary workstation and web server.
- **IIS (Internet Information Services)**: Enabled with CGI to host the web application.
- **PHP 7.4 & MySQL**: Essential for processing application scripts and storing ticket data.
- **osTicket Files**: Core application files configured within the web server directory.

<h2>Installation Steps</h2>
Step 1: Setting up the Virtual Workspace

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before installing software, you need a place for it to live. Use your Microsoft Azure lab to create a Windows 10 Virtual Machine. This acts as your dedicated office server.
</p>
<br />
Step 2: Preparing the Web Server (IIS)
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Computers don't know how to host websites by default. You have to enable Internet Information Services (IIS) in Windows Features.
</p>
<br />
Step 3: Installing the "Translators" (PHP)
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The ticketing system is written in a language called PHP. Since Windows doesn't speak PHP naturally, you have to install it and use PHP Manager to link it to the web server.
</p>
<br />
Step 2: Preparing the Web Server (IIS)
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Computers don't know how to host websites by default. You have to enable Internet Information Services (IIS) in Windows Features.
</p>
