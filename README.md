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
  - Log in to the Azure portal and create a Virtual Machine with the specified configuration.
  - Connect to the VM using Remote Desktop with the provided credentials. 
<p>
<img width="1725" height="383" alt="Screenshot 2026-02-25 201353" src="https://github.com/user-attachments/assets/feca116a-b432-4ebc-a037-d7fa142c5b4d" />
<img width="1777" height="972" alt="Screenshot 2026-02-25 201828" src="https://github.com/user-attachments/assets/34e023d4-ec87-4009-ac6c-4e9366a21136" />

### Step 2: Prepare the Virtual Machine
  - Inside the VM, download [osTicket-Installation-Files.zip](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD) to the desktop.
  - Extract the files into a folder named `osTicket-Installation-Files` on the desktop.
<img width="443" height="233" alt="Screenshot 2026-02-25 203600" src="https://github.com/user-attachments/assets/5a450298-7939-4f46-bc5d-d4797d16fcbe" />
<img width="630" height="455" alt="Screenshot 2026-02-25 203933" src="https://github.com/user-attachments/assets/833aabcc-ccbf-4c72-abfd-bab234ad416c" />


### 3. Install and Enable IIS with CGI
1. Open **Control Panel** -> **Programs** -> **Turn Windows features on or off**.
2. Enable the following:
   - **Internet Information Services (IIS)**
   - **World Wide Web Services** -> **Application Development Features** -> **[X] CGI**
<img width="700" height="458" alt="Screenshot 2026-02-25 204931" src="https://github.com/user-attachments/assets/147313fd-1da4-4a6f-b4da-fd54f3a90583" />


### 4. Install Required Components
From the `osTicket-Installation-Files` folder, perform the following installations:
1. Install **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`).
2. Install **Rewrite Module** (`rewrite_amd64_en-US.msi`).
<img width="514" height="309" alt="Screenshot 2026-02-25 205346" src="https://github.com/user-attachments/assets/5e9dfe40-aa10-4ef5-921f-ab2851c63777" />
<img width="347" height="280" alt="Screenshot 2026-02-25 205418" src="https://github.com/user-attachments/assets/b4e8c211-76a6-487d-a38b-2804ca27cbcd" />
<img width="510" height="414" alt="Screenshot 2026-02-25 205529" src="https://github.com/user-attachments/assets/ef66d70a-dd3c-4d1c-b266-bc0aebd490cc" />



### 5. Set Up PHP
1. Create the directory `C:\PHP`.
2. Extract `PHP 7.3.8` (`php-7.3.8-nts-Win32-VC15-x86.zip`) into the `C:\PHP` folder.
3. Install **VC_redist.x86.exe**.
<img width="367" height="377" alt="Screenshot 2026-02-25 210448" src="https://github.com/user-attachments/assets/3c52d019-3e7e-4248-b957-fd2cc3762174" />
<img width="716" height="609" alt="Screenshot 2026-02-25 211127" src="https://github.com/user-attachments/assets/ca009ad4-d59f-4d3e-9b5b-dd332173a13f" />
<img width="506" height="369" alt="Screenshot 2026-02-25 211330" src="https://github.com/user-attachments/assets/9f7f258a-abb9-4589-b32b-95f12594803a" />



### 6. Install MySQL
1. Install **MySQL 5.5.62** (`mysql-5.5.62-win32.msi`) with the following configuration:
   - Choose **Typical Setup**.
   - Launch the **Configuration Wizard** after installation.
   - Select **Standard Configuration**.
   - Set MySQL credentials:
     - Username: `root`
     - Password: `root`
<img width="671" height="422" alt="Screenshot 2026-02-25 212430" src="https://github.com/user-attachments/assets/fab912d1-009f-4d62-b3c6-45734bce41df" />
<img width="492" height="380" alt="Screenshot 2026-02-25 212511" src="https://github.com/user-attachments/assets/30de4881-da78-4a92-88d2-6afe07c74631" />
<img width="492" height="374" alt="Screenshot 2026-02-25 212654" src="https://github.com/user-attachments/assets/a2e884e1-6ad1-43be-bf1d-31b469cfabb3" />
<img width="491" height="377" alt="Screenshot 2026-02-25 212834" src="https://github.com/user-attachments/assets/b7c99ea2-c805-4057-a270-6b2eeeac4024" />


### 7. Configure IIS
1. Open IIS as an Administrator.
2. Register PHP:
   - Open **PHP Manager** in IIS.
   - Register `C:\PHP\php-cgi.exe`.
3. Reload IIS:
   - Open IIS.
   - Stop and Start the server.
<img width="437" height="284" alt="Screenshot 2026-02-25 213155" src="https://github.com/user-attachments/assets/b6cdab43-b90b-4db1-a4fe-0a35169571dc" />
<img width="664" height="446" alt="Screenshot 2026-02-25 213519" src="https://github.com/user-attachments/assets/58ef2f59-43b6-4d57-b0c6-60b5b7a5f820" />


### 8. Install osTicket
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
  
<img width="494" alt="Screenshot 2025-01-22 at 8 55 53 PM" src="https://github.com/user-attachments/assets/b2a66cbb-bada-4031-8445-9d2e38c84897" />
<img width="346" alt="Screenshot 2025-01-22 at 8 56 16 PM" src="https://github.com/user-attachments/assets/2a361498-b828-4fd1-93e3-88f0384427e0" />
<img width="577" alt="Screenshot 2025-01-22 at 8 57 11 PM" src="https://github.com/user-attachments/assets/5525f530-b204-4472-906d-ff326056ecdc" />
<img width="415" alt="Screenshot 2025-01-22 at 8 57 44 PM" src="https://github.com/user-attachments/assets/9421699b-142a-49da-9abf-43f523954ac3" />
<img width="415" alt="Screenshot 2025-01-22 at 8 58 46 PM" src="https://github.com/user-attachments/assets/d5e062b6-e77a-4cba-bb1c-0d8af4b17e23" />

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

<img width="413" alt="Screenshot 2025-01-22 at 9 00 07 PM" src="https://github.com/user-attachments/assets/2bcbebe8-8fb2-467e-b880-d055a461df7e" />
<img width="473" alt="Screenshot 2025-01-22 at 9 05 34 PM" src="https://github.com/user-attachments/assets/c33af950-e50a-4b8b-adb4-4fff4c6f2a90" />
<img width="625" alt="Screenshot 2025-01-22 at 9 05 49 PM" src="https://github.com/user-attachments/assets/c8fcfd0a-9528-4eba-b768-b4e23027912f" />
<img width="500" alt="Screenshot 2025-01-22 at 9 06 11 PM" src="https://github.com/user-attachments/assets/728f3790-c646-49d4-93d1-f71b82e372ea" />
<img width="536" alt="Screenshot 2025-01-22 at 9 06 30 PM" src="https://github.com/user-attachments/assets/89ab1176-e1c9-4724-ae6a-1461dbfdb155" />
<img width="612" alt="Screenshot 2025-01-22 at 9 06 47 PM" src="https://github.com/user-attachments/assets/386abce2-b4d4-4484-bdfb-8a4f1aff1f85" />

### 11. Post-Installation Cleanup
1. Delete the `C:\inetpub\wwwroot\osTicket\setup` folder.
2. Set `C:\inetpub\wwwroot\osTicket\include\ost-config.php` to **Read-only** permissions.

### 12. Access osTicket
- Admin Panel: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)
- End-User Portal: [http://localhost/osTicket/](http://localhost/osTicket/)

## Conclusion
Following these steps, you should have a fully functional osTicket installation. Enjoy managing your help desk with osTicket!
