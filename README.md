<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

You can find all the necessary installation files for this project below:  
[Download Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure subscription
- Azure Virtual Machine with the following configuration:
  - OS: Windows 10
  - vCPUs:4
  - Name: osticket-vm
  - Username:
  - Password:
- Remote Desktop Client

<h2>Installation Steps</h2>

### Step 1: Create and Configure the Azure Virtual Machine
I logged into the Microsoft Azure portal and deployed a Virtual Machine using the specified configuration. After the deployment was completed, I securely connected to the VM using Remote Desktop Protocol (RDP) with the assigned credentials to begin system configuration.
<p>
<img width="1725" height="383" alt="Screenshot 2026-02-25 201353" src="https://github.com/user-attachments/assets/feca116a-b432-4ebc-a037-d7fa142c5b4d" />
<img width="1777" height="972" alt="Screenshot 2026-02-25 201828" src="https://github.com/user-attachments/assets/34e023d4-ec87-4009-ac6c-4e9366a21136" />

### Step 2: Prepare the Virtual Machine
Within the virtual machine, I downloaded the required osTicket Installation Files
and saved them locally to the desktop. I then extracted the contents into a structured directory named `osTicket-Installation-Files`, ensuring all required installation dependencies and components were properly organized before application deployment.

<img width="443" height="233" alt="Screenshot 2026-02-25 203600" src="https://github.com/user-attachments/assets/5a450298-7939-4f46-bc5d-d4797d16fcbe" />
<img width="630" height="455" alt="Screenshot 2026-02-25 203933" src="https://github.com/user-attachments/assets/833aabcc-ccbf-4c72-abfd-bab234ad416c" />


### 3. Install and Enable IIS with CGI
I accessed the Windows Control Panel and navigated to Programs → Turn Windows features on or off to enable the required web server components. I activated Internet Information Services (IIS) and enabled CGI under World Wide Web Services → Application Development Features to support PHP processing and prepare the server environment for osTicket deployment.

<img width="700" height="458" alt="Screenshot 2026-02-25 204931" src="https://github.com/user-attachments/assets/147313fd-1da4-4a6f-b4da-fd54f3a90583" />


### 4. Install Required Components
From the `osTicket-Installation-Files` folder, perform the following installations:
I installed **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`) and installed **Rewrite Module** (`rewrite_amd64_en-US.msi`).

<img width="514" height="309" alt="Screenshot 2026-02-25 205346" src="https://github.com/user-attachments/assets/5e9dfe40-aa10-4ef5-921f-ab2851c63777" />
<img width="347" height="280" alt="Screenshot 2026-02-25 205418" src="https://github.com/user-attachments/assets/b4e8c211-76a6-487d-a38b-2804ca27cbcd" />
<img width="510" height="414" alt="Screenshot 2026-02-25 205529" src="https://github.com/user-attachments/assets/ef66d70a-dd3c-4d1c-b266-bc0aebd490cc" />



### 5. Set Up PHP
I created a dedicated directory at `C:\PHP` to host the PHP runtime environment and extracted `PHP 7.3.8` (`php-7.3.8-nts-Win32-VC15-x86.zip`) into this location to ensure proper server-side scripting support. I then installed the **VC_redist.x86.exe** to satisfy runtime dependencies necessary for PHP to function correctly within the IIS environment.
 
<img width="367" height="377" alt="Screenshot 2026-02-25 210448" src="https://github.com/user-attachments/assets/3c52d019-3e7e-4248-b957-fd2cc3762174" />
<img width="716" height="609" alt="Screenshot 2026-02-25 211127" src="https://github.com/user-attachments/assets/ca009ad4-d59f-4d3e-9b5b-dd332173a13f" />
<img width="506" height="369" alt="Screenshot 2026-02-25 211330" src="https://github.com/user-attachments/assets/9f7f258a-abb9-4589-b32b-95f12594803a" />



### 6. Install MySQL
I installed **MySQL 5.5.62** (`mysql-5.5.62-win32.msi`) using the standard configuration option and completed the post-installation Configuration Wizard using the Standard Configuration method. During setup, I configured the database administrative credentials, Username: `root` and Password: `root`  to establish secure access and prepare the relational database environment required for the osTicket application.

<img width="671" height="422" alt="Screenshot 2026-02-25 212430" src="https://github.com/user-attachments/assets/fab912d1-009f-4d62-b3c6-45734bce41df" />
<img width="492" height="380" alt="Screenshot 2026-02-25 212511" src="https://github.com/user-attachments/assets/30de4881-da78-4a92-88d2-6afe07c74631" />
<img width="492" height="374" alt="Screenshot 2026-02-25 212654" src="https://github.com/user-attachments/assets/a2e884e1-6ad1-43be-bf1d-31b469cfabb3" />
<img width="491" height="377" alt="Screenshot 2026-02-25 212834" src="https://github.com/user-attachments/assets/b7c99ea2-c805-4057-a270-6b2eeeac4024" />


### 7. Configure IIS
I launched Internet Information Services (IIS) with administrative privileges and used PHP Manager to register the PHP executable `C:\PHP\php-cgi.exe`, enabling IIS to process PHP-based applications. After completing the configuration, I restarted the IIS service to apply the changes and ensure the web server properly recognized the newly registered PHP runtime.

<img width="437" height="284" alt="Screenshot 2026-02-25 213155" src="https://github.com/user-attachments/assets/b6cdab43-b90b-4db1-a4fe-0a35169571dc" />
<img width="664" height="446" alt="Screenshot 2026-02-25 213519" src="https://github.com/user-attachments/assets/58ef2f59-43b6-4d57-b0c6-60b5b7a5f820" />


### 8. Install osTicket
I extracted `osTicket v1.15.8` from the `osTicket-Installation-Files` and deployed the application files to the IIS web root directory `C:\inetpub\wwwroot`. The `upload` directory was renamed to `osTicket` to align with the intended site structure. After reloading IIS, I verified the deployment by navigating to **Sites** -> **Default** -> **osTicket** within IIS Manager and browsing over **Browse *:80**. To resolve initial dependency warnings, I enabled the required PHP extensions `php_imap.dll` `php_intl.dll` `php_opcache.dll` through PHP Manager to ensure full application compatibility and functionality.







1. Extract `osTicket v1.15.8` (`osTicket-v1.15.8.zip`) from the `osTicket-Installation-Files` folder.
2. Copy the `upload` folder to `C:\inetpub\wwwroot`.
3. Rename the folder from `upload` to `osTicket`.
4. Reload IIS.
5. In IIS:
   - Navigate to **Sites** -> **Default** -> **osTicket**.
   - On the right-hand side, click **Browse *:80**.
6. Address missing extensions:
   - Navigate to **PHP Manager** in IIS.
   - Enable the following extensions:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`
7. Refresh the osTicket site in your browser.
<img width="738" height="595" alt="Screenshot 2026-02-25 215053" src="https://github.com/user-attachments/assets/9d7ce37c-d5bd-4a34-803f-e633e9e531b0" />
<img width="399" height="380" alt="Screenshot 2026-02-25 215219" src="https://github.com/user-attachments/assets/a07e1d6d-20f0-4a38-923e-fe02fa305e63" />
<img width="185" height="140" alt="Screenshot 2026-02-25 215236" src="https://github.com/user-attachments/assets/f744abc2-5f24-4786-81ea-bcb563802a36" />
<img width="1340" height="401" alt="Screenshot 2026-02-25 215727" src="https://github.com/user-attachments/assets/30602cc8-c66f-4a29-bdfb-1ab5aebbde26" />
<img width="658" height="769" alt="Screenshot 2026-02-25 220244" src="https://github.com/user-attachments/assets/85ec4e84-b045-43cb-9a4a-325e4b82b7d0" />
<img width="601" height="722" alt="Screenshot 2026-02-25 220348" src="https://github.com/user-attachments/assets/a687e7c8-1a14-4ad5-9565-f472205e851b" />

### 9. Configure osTicket
1. Rename `ost-config.php`:
   - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
   - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
2. Assign permissions to `ost-config.php`:
   - Disable inheritance -> Remove all permissions.
   - Add new permissions: `Everyone -> Full Control`.
3. Continue setup in the browser:
   - Name your help desk.
   - Set a default email for receiving customer emails.
  
<img width="565" height="417" alt="Screenshot 2026-02-26 170628" src="https://github.com/user-attachments/assets/dea38f7b-2ea5-49e9-93dc-d599b76210c0" />
<img width="206" height="152" alt="Screenshot 2026-02-26 170651" src="https://github.com/user-attachments/assets/440860c8-d3bd-45c5-9b01-8ea1511438bd" />
<img width="481" height="312" alt="Screenshot 2026-02-26 171317" src="https://github.com/user-attachments/assets/cfac16a4-991d-47d3-9889-f9fd3c0c01dd" />
<img width="819" height="798" alt="Screenshot 2026-02-26 172822" src="https://github.com/user-attachments/assets/f9bad7e5-798a-49c8-9a8e-2a631ca0fe02" />



### 10. Set Up the Database
1. Install **HeidiSQL** from the `osTicket-Installation-Files` folder.
2. Open HeidiSQL and create a new session:
   - Username: `root`
   - Password: `root`
3. Create a database named `osTicket`.
4. Complete the setup in the browser:
   - MySQL Database: `osTicket`
   - MySQL Username: `root`
   - MySQL Password: `root`
   - Click **Install Now!**

<img width="788" height="480" alt="Screenshot 2026-02-26 173629" src="https://github.com/user-attachments/assets/a9bebdf3-65ec-49df-9673-51978f3be9a8" />
<img width="677" height="475" alt="Screenshot 2026-02-26 173837" src="https://github.com/user-attachments/assets/1ec230f6-8975-4099-b9d9-62e73007237d" />
<img width="610" height="419" alt="Screenshot 2026-02-26 174230" src="https://github.com/user-attachments/assets/435d8ec8-bc60-47ad-85fc-94caa27a93e5" />
<img width="567" height="372" alt="Screenshot 2026-02-26 174412" src="https://github.com/user-attachments/assets/d8fd3791-ba50-4356-8ac6-61dfbd74bf21" />
<img width="814" height="611" alt="Screenshot 2026-02-26 174503" src="https://github.com/user-attachments/assets/88df8713-1eeb-41ea-99d3-c052b6238ac6" />


### 11. Post-Installation Cleanup
1. Delete the `C:\inetpub\wwwroot\osTicket\setup` folder.
2. Set `C:\inetpub\wwwroot\osTicket\include\ost-config.php` to **Read-only** permissions.

### 12. Access osTicket
- Admin Panel: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)
- End-User Portal: [http://localhost/osTicket/](http://localhost/osTicket/)

## Conclusion
Following these steps, you should have a fully functional osTicket installation. Enjoy managing your help desk with osTicket!
