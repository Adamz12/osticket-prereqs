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

<p>
<img src="https://i.imgur.com/fwW6pPo.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open File Explorer, navigate to the C: drive, right-click in the blank area, choose New → Folder, name it php, and press Enter. This directory will hold your PHP binaries.
</p>

<p>
<img src="https://i.imgur.com/wOG3NLE.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Extract the php-7.3.8-nts-Win32-VC15-x86.zip archive from your osTicket-Installation-Files folder directly into C:\php so that all PHP files unpack into that directory.
</p>

<p>
<img src="https://i.imgur.com/v8Irx7E.jpeg" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the osTicket-Installation-Files folder, double-click VC_redist.x86.exe, and follow the installer’s on-screen instructions. This installs the required Visual C++ runtime for PHP.
</p>

<p>
<img src="https://i.imgur.com/ZX2MQqJ.jpeg" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the osTicket-Installation-Files folder, double-click mysql-5.5.62-win32.msi, select Typical Setup, ensure Launch Configuration Wizard is checked, and complete the install. In the Configuration Wizard choose Standard Configuration, set Username to root and Password to root, then finish the wizard.
</p>

<p>
<img src="https://i.imgur.com/zH9KaYF.jpeg" alt="Disk Sanitization Steps"/>
</p>
<p>
Open IIS Manager with administrative rights, then click PHP Manager. Choose Register new PHP version, click the browse button (⋯), navigate to C:\PHP\php-cgi.exe, and click OK. Finally, restart IIS by selecting the server node and clicking Stop then Start in the Manage Server panel.
</p>

<p>
<img src="https://i.imgur.com/ULH9hAm.png" alt="Disk Sanitization Steps"/>
</p>
<p>
In the osTicket-Installation-Files folder, unzip osTicket-v1.15.8.zip within the same folder. Then copy the resulting upload folder within the osTicket-v1.15.8.zip into C:\inetpub\wwwroot, and rename that folder to "osTicket".
</p>

<p>
<img src="https://i.imgur.com/xjMMjdI.jpeg" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, restart IIS to pick up the new files. In IIS Manager, select your server in the left pane, then click Stop in the right-hand Manage Server panel. Once it’s stopped, click Start to bring IIS back online. This ensures your freshly deployed osTicket site is served correctly.
</p>

<p>
<img src="https://i.imgur.com/1IuWfZc.jpeg" alt="Disk Sanitization Steps"/>
</p>
<p>
Open IIS Manager, expand Sites in the left tree, select the osTicket site, and then click *Browse :80 in the Actions pane. Your default browser will launch and load the osTicket setup page.
</p>

<p>
<img src="https://i.imgur.com/WIAc7yb.jpeg" alt="Disk Sanitization Steps"/>
</p>
<p>
If any PHP extensions are missing on the osTicket home page, open IIS Manager, expand Sites → osTicket, then double-click PHP Manager. In Enable or Disable Extensions, check php_imap.dll, php_intl.dll, and php_opcache.dll, click Apply, and finally restart the site (or IIS) to load the new extensions.
</p>

<p>
<img src="https://i.imgur.com/OXKbrmH.jpeg" alt="Disk Sanitization Steps"/>
</p>
<p>
Open File Explorer and navigate to C:\inetpub\wwwroot\osTicket\include. Right-click ost-sampleconfig.php, choose Rename, and change the filename to ost-config.php. This creates your active configuration file for osTicket.
</p>


