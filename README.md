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

<b>Register PHP in IIS </b>

- Open IIS Manager as Administrator.
  <img width="975" height="686" alt="image" src="https://github.com/user-attachments/assets/8070e5b2-b8d1-4267-885d-ee643082b4d1" />

- Open <b>PHP Manager → Register new PHP version</b>.
- Browse to <b>C:\PHP\php-cgi.exe</b> and select it.
  <img width="975" height="393" alt="image" src="https://github.com/user-attachments/assets/3b77a3a4-9da2-4027-b366-b92deb0d0e5c" />

- Restart IIS (Stop and Start server)

<b>Extract and Move osTicket Files to IIS</b>

- From the extracted osTicket files, open the upload folder.
- Copy it into C:\inetpub\wwwroot.
- Rename the folder from upload to osTicket (no spaces, exact casing).

  <img width="492" height="348" alt="image" src="https://github.com/user-attachments/assets/601138b2-4bc2-4cab-aa4f-aa135de30558" />

  <img width="975" height="221" alt="image" src="https://github.com/user-attachments/assets/eac28a30-72c3-4e5f-96cc-e7915e743c9d" />

- Restart IIS again

<b>Verify osTicket in Browser</b>
- In IIS, expand Sites → Default Site → osTicket.
- Click Browse in the Actions pane.
- The osTicket setup page should load.
- If errors occur, verify folder names and IIS configuration

  <img width="975" height="910" alt="image" src="https://github.com/user-attachments/assets/433f724e-eb1d-4e8f-9bb8-b4b0b64ba206" />

<b>Enable PHP Extensions in IIS</b>
- In IIS, go to Sites → Default Site → osTicket → PHP Manager.
- Enable the following extensions:
 - php_imap.dll (mail fetching)
 -  php_intl.dll (localization)
 -  php_opcache.dll (performance)

   <img width="577" height="949" alt="image" src="https://github.com/user-attachments/assets/3a2141d4-1155-48f0-ac80-9f0d6cd47e16" />
   <img width="975" height="957" alt="image" src="https://github.com/user-attachments/assets/4bc5bd4c-8237-4c04-b302-37ed33c75e84" />

   <b>Rename osTicket Configuration File</b>

   - Navigate to C:\inetpub\wwwroot\osTicket\include.
   - Rename ost-sampleconfig.php to ost-config.php.
   - Right-click the file → Properties → Security → Advanced.
   - Remove inherited permissions.
   - Add Everyone with Full Control (lab only, not secure for production)

<img width="975" height="603" alt="image" src="https://github.com/user-attachments/assets/2aff11cd-f04f-4fbe-9412-2131875195e0" />

<img width="975" height="700" alt="image" src="https://github.com/user-attachments/assets/e16d7924-374d-4a00-abcd-633732fea02b" />

<b>Configure osTicket Admin Account</b>

- Back in the browser setup page, enter:
  - Helpdesk Name (any value)
  - Admin Username: adminuser
  - Password: Password1
  - Email addresses (any values)
 
<img width="975" height="1245" alt="image" src="https://github.com/user-attachments/assets/e103c507-e677-4f17-acef-5ee82b1103ce" />

<b>Create osTicket Database in MySQL with HeidiSQL</b>

- From installation files, install HeidiSQL.
<img width="975" height="737" alt="image" src="https://github.com/user-attachments/assets/14c9b3ce-3be9-4b05-a794-765faf6a9b01" />

<img width="975" height="751" alt="image" src="https://github.com/user-attachments/assets/821c7798-3f00-439a-9a7a-1ba4fc38ed03" />

- Create a new session with username: root, password: root.
- Connect and create a new database named osTicket.
- Return to the browser setup and fill in:
  - Database Name: osTicket
  - MySQL Username: root
  - Password: root
  <img width="975" height="494" alt="image" src="https://github.com/user-attachments/assets/61aa6a74-ca32-4edd-b328-dcfc8a70c095" />

  - Click Install Now
  - Successful Installation:
    <img width="717" height="553" alt="image" src="https://github.com/user-attachments/assets/7ca27586-19fc-4b10-92c6-2099e3041e76" />

    <b>Verify Installation and Login</b>

    - In HeidiSQL, refresh to confirm new tables were created in the osTicket database.
      <img width="975" height="624" alt="image" src="https://github.com/user-attachments/assets/8ff49c4f-a9d2-4489-8b77-2d4971eaeb5e" />

    - In browser, navigate to: Admin login page: use adminuser / Password1 after Logging in
      <img width="975" height="374" alt="image" src="https://github.com/user-attachments/assets/dd659f21-c23b-4afe-95ea-f814eb9c7028" />

- End-user page: allows ticket submission.
  <img width="868" height="501" alt="image" src="https://github.com/user-attachments/assets/7565f7f3-2010-4d51-980e-3d627c8bea4a" />


















  



  


















  

  
  







    



  












 




