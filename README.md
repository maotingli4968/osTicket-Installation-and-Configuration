<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines / Compute)
- Remote Desktop Protocol (RDP)
- IIS (Internet Information Services) with CGI
- PHP Manager for IIS
- MySQL 5.5.62
- HeidiSQL (Database Client)


<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Azure subscription
- A new Resource Group in Azure
- Windows 10 Virtual Machine with at least:
    - 2 vCPUs
    - 8 GB RAM
- Remote Desktop access enabled
- osTicket installation files (downloaded within VM)

<h2>Installation Steps</h2>

<b> Create a Windows VM in Azure</b> 

- Log into the Azure Portal and create a new Resource Group.
- Create a Virtual Machine named osTicket-VM.
- Use Windows 10 Pro as the image, with at least 2 vCPUs and 8 GB RAM.
- Username && Password that are unique to you
- Allow Azure to create a new virtual network.
- Review and create the VM


<b>Connect to VM Using Remote Desktop</b>

- Copy the VM’s public IP address from the Azure Portal.
- Open Remote Desktop, add a PC, and connect with the credentials
- If login fails, reset the password in the Azure Portal under <b>VM → Help → Reset Password</b>

If you have any problems regarding creating and logging into a Windows-VM, please refer to my previous posts for detailed explanation. 

<b>Download and Extract osTicket Installation Files</b>

- Inside the VM, open Microsoft Edge and download the <b>osTicket installation zip file</b>.
  <img width="870" height="311" alt="image" src="https://github.com/user-attachments/assets/da2daee4-fc3e-4e4a-95df-06cedd42d137" />

- Move the file to the Desktop, right-click → Extract All, and extract into a folder named <b>osTicket files</b> on the Desktop.
  <img width="408" height="470" alt="image" src="https://github.com/user-attachments/assets/9c8ff16e-813c-428a-b6dd-04ee7fe23e8c" />

  <b>Enable IIS and CGI in Windows</b>

  - Open<b> Control Panel → Programs → Turn Windows Features on or off</b>

    <img width="975" height="666" alt="image" src="https://github.com/user-attachments/assets/c6e24619-0d15-4ad5-9fec-78f56d2d1fba" />

  - Enable <b>Internet Information Services (IIS)</b>.

  <img width="975" height="865" alt="image" src="https://github.com/user-attachments/assets/a15ccbc8-abeb-4e32-b15d-b19349e8fbda" />

  - Expand World Wide Web Services → Application Development Features.
  - Check CGI.

    <img width="975" height="882" alt="image" src="https://github.com/user-attachments/assets/a0613550-f95e-4199-ac1e-285b91696f5f" />
  - Confirm and let IIS install
    <img width="975" height="783" alt="image" src="https://github.com/user-attachments/assets/c080a961-51e3-4a37-98bd-00114c9edfbf" />

    <b>Test IIS Installation</b>

 - Open a browser in the VM and type 127.0.0.1.
 - You should see the IIS default webpage, confirming the web server is working.

<img width="975" height="604" alt="image" src="https://github.com/user-attachments/assets/8735fc7f-a1e2-443e-bee3-f33c813fcf9d" />

<b> Install PHP Manager and Rewrite Module</b>

- From the <b>osTicket installation files</b> folder, install <b>PHP Manager for IIS</b>.
  <img width="975" height="805" alt="image" src="https://github.com/user-attachments/assets/7b2bd793-0a27-42ee-b72a-5ebfb4eff13c" />
- Install the <b>Rewrite Module from the same folder</b>.
  <img width="975" height="746" alt="image" src="https://github.com/user-attachments/assets/8fa1c4c0-8e9f-4b0f-933e-3c0633b649d4" />


  Both are required dependencies for osTicket.


<b>Create PHP Directory and Extract Files</b>
- Create a new folder C:\PHP.
<img width="975" height="425" alt="image" src="https://github.com/user-attachments/assets/aad19fd7-c301-4d7a-8658-3c7800968222" />

- From the installation files, extract the PHP 7.3.8 package into this folder.
<img width="975" height="782" alt="image" src="https://github.com/user-attachments/assets/4f78f8a8-af57-46c2-a082-36a786a1b559" />

- Verify that the folder contains the PHP executables and libraries


<b> Install VC++ Redistributable</b>

- From the installation files, run the VC++ redistributable installer.
- This is another required component for osTicket

<img width="975" height="565" alt="image" src="https://github.com/user-attachments/assets/e47218a2-4865-46d1-bd90-4d6f6c6ab423" />

<b>Install MySQL 5.5.62</b>

- Run the MySQL installer from the installation files.
- Choose Typical Setup.
- Launch the Configuration Wizard → select Standard Configuration.

<img width="975" height="753" alt="image" src="https://github.com/user-attachments/assets/853c198b-efe5-4ad0-a958-2cea70ff1f8b" />

- Set both username and password to <b>root</b>.
<img width="975" height="730" alt="image" src="https://github.com/user-attachments/assets/b4cf4d91-36a7-43d0-993a-9525c1c1e7eb" />

- Save credentials in a Notepad file on the Desktop for later use












  

  
  







    



  












 




<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
