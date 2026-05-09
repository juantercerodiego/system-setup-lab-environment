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

- Windows 11 

<h2>List of Prerequisites</h2>

- **Microsoft Azure Subscription**: Used to host the virtual server environment.
- **Windows 10 VM**: Deployed as the primary workstation and web server.
- **IIS (Internet Information Services)**: Enabled with CGI to host the web application.
- **PHP 7.4 & MySQL**: Essential for processing application scripts and storing ticket data.
- **osTicket Files**: Core application files configured within the web server directory.

<h2>Installation Steps</h2>
<h2>Step 1: Setting up the Virtual Workspace</h2>

<p>
<img width="1192" height="476" alt="step 1 osticket" src="https://github.com/user-attachments/assets/1771b82f-edb9-4613-bb19-61e5321b2d88" />

</p>
<p>
Before installing software, you need a place for it to live. Use your Microsoft Azure lab to create a Windows 10 Virtual Machine. This acts as your dedicated office server.
</p>
<br />
<h2>Step 2: Preparing the Web Server (IIS)</h2>
<p>
<img width="647" height="493" alt="step 2" src="https://github.com/user-attachments/assets/4b008e5f-5591-4361-aee3-465137420484" />
</p>
<p>
Computers don't know how to host websites by default. You have to enable Internet Information Services (IIS) in Windows Features.
</p>
<br />
<h2>Step 3: Installing the "Translators" (PHP)</h2>
<p>
<img width="951" height="510" alt="step 3" src="https://github.com/user-attachments/assets/d9c3ee16-3b5d-4db7-8500-6e9c2b7b36c4" />

</p>
<p>
The ticketing system is written in a language called PHP. Since Windows doesn't speak PHP naturally, you have to install it and use PHP Manager to link it to the IIS web server.
</p>
<br />
<h2>Step 4: Building the Filing Cabinet (MySQL)</h2>
<p>
<img width="980" height="598" alt="step4" src="https://github.com/user-attachments/assets/445a572f-782c-41a7-b1e7-136735e64e7f" />

</p>
<p>
Every help desk needs a place to save information like ticket numbers and user messages. I used a tool called HeidiSQL to create a private database named "osticket." Think of this as the digital filing cabinet where the system securely stores and organizes everything so nothing gets lost.
</p>
<br />
<h2>Step 5: (Final Install & Success)</h2>
<p>
<img width="1110" height="598" alt="step 5" src="https://github.com/user-attachments/assets/38617844-3423-422d-8c7b-501aec1c7fbe" />

</p>
<p>
After getting the "engine" (PHP) and the "filing cabinet" (MySQL) ready, I finally hit the ignition. I finished the setup through my browser and landed on the success screen. This proves the help desk is officially live, working perfectly, and ready to start handling real support tickets!
</p>
