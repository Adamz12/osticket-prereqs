<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidl SQL


<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/XDHSAve.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I started by provisioning an Azure VM in the osticket resource group named osticket-vm, choosing the Standard_D4s_v3 SKU (4 vCPUs, 16 GiB RAM) on Windows 10 Pro 22H2. This setup gives me a dedicated, high-performance environment for IIS, PHP, and MySQL while keeping my physical workstation isolated and secure.
</p>
<br />

<p>
<img src="https://i.imgur.com/k3NaUIz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I retrieved the VM’s public IP from the Azure portal and opened Microsoft Remote Desktop on my Mac. I created a new connection named “osticket-vm” pasted the IP into the PC name field, and used my admin credentials to log in.
</p>
<br />

<p>
<img src="https://i.imgur.com/5lhvNkZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I downloaded the latest osTicket release from the official GitHub repository, extracted the ZIP archive, renamed the resulting folder to osTicket-Installation-Files, and placed it on my desktop for easy access during the setup.
</p>
<br />

<p>
<img src="https://i.imgur.com/5peaeXs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I enabled the CGI module in IIS so PHP-CLI scripts and other CGI applications would run. I opened Control Panel, navigated to Programs → Programs and Features, and clicked Turn Windows features on or off. In the Windows Features dialog, I expanded Internet Information Services → World Wide Web Services → Application Development Features, checked CGI, and clicked OK. Windows then installed the CGI feature
</p>

<p>
<img src="https://i.imgur.com/VeV2uQZ.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the osTicket-Installation-Files folder on the desktop, double-click PHPManagerForIIS_V1.5.0.msi, and follow the installer’s on-screen instructions. When the setup finishes, PHP Manager will appear in the IIS console for PHP configuration.
</p>

<p>
<img src="https://i.imgur.com/DnV6KB8.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the osTicket-Installation-Files folder on the desktop, double-click rewrite_amd64_en-US.msi, and follow the on-screen prompts. After installation, the URL Rewrite option will appear in the IIS console.
</p>

