<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

<a href="https://youtu.be/_XGpWhQGhZQ">Video Guide</a> (Reccomended)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b>

<h2>List of Prerequisites</h2>

- <a href="https://github.com/osTicket/osTicket">osTicket</a>
- <a href="https://www.php.net/">PHP</a>
- <a href="https://www.heidisql.com">HeidiSQL</a> (or another MySQL interface)
- <a href="https://www.mysql.com/">MySQL database</a>
- <a href="https://www.iis.net/">HTTP server using Microsoft IIS</a>

<h2>Installation Steps</h2>

<p>
  
  
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/81ea8226-1b0f-4443-938d-432e6a702e5d" />
</p>
<p>
Enable IIS in Windows with CGI.
You can find this in 
<br/>
Control Panel -> Uninstall a program -> Turn windows features on or off -> Internet Information Services -> World Wide Web Services -> Application Development Features -> CGI
<br/>
  This allows for osTicket to run in a local web server on your computer.
</p>
<br />

<p>
<img width="462" height="133" alt="image" src="https://github.com/user-attachments/assets/81efa0e9-1591-4510-a214-5918162bd52c" />
</p>
<p>
Install Dependencies:
<br/>
<a href="https://github.com/phpmanager/phpmanager/releases">PHP Manager for IIS (x64 .msi)</a>
<br/>
<a href="https://www.iis.net/downloads/microsoft/url-rewrite">Rewrite Module (x64 .msi)</a>
<br/>
<a href="https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-supported-redistributable-version">Visual C++ Redistributable (x64 .exe)</a>
<br/>
<a href="https://dev.mysql.com/downloads/mysql/">MySQL (x64 .zip Non Thread Safe)</a>
<br/>
Create a directory in C:\PHP and unzip <a href="https://www.php.net/downloads.php">PHP (x64 .msi)</a> into it
</p>
<br />

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f0a4a2b3-9087-4335-912f-2191536f7eac" />
</p>
<p>
Open IIS as an Admin.
<br/>
Register PHP in the IIS. Double click "PHP Manager" -> Register new PHP version -> Path to "C:\PHP\php-cgi"
<br/>
Reload the web server by right clicking the server in the top left stopping, then starting.
<br/>
Unzip <a href="https://github.com/osTicket/osTicket/releases/">osTicket</a> and copy the upload folder into C:\inetpub\wwwroot
<br/>
Rename "upload" to "osTicket" EXACTLY. (This directly affects the url used to connect to your osTicket installation.)
<br/>
Restart the web server again
</p>
<br />

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/51608ba6-cfa8-4ed8-ac03-e783a59838e0" />
</p>
<p>
Reopen IIS then on the left, click sites -> Default -> osTicket -> on the right, click "Browse *:80" to open the site.
</p>
<br/>

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/48f35471-8b5e-4f03-a6bb-ced4fb636f0f" />
</p>
<p>
To enable the intl extension for improved localization, in IIS go to sites -> Default -> osTicket
<br/>
Double click PHP Manager
<br/>
Click "Enable or disable an extension". Enable "php_intl.dll"
<br/>
Reload the web server by right clicking the server in the top left stopping, then starting.
<br/>
The <a href="https://pecl.php.net/package/imap">Imap</a> extension is used for email processing. However, it is no longer required due to different methods used for email. 
<br/>
The <a href="https://pecl.php.net/package/APCu">APCu</a> extension improves performance.
</p>
<br />

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9aa1cdf4-699a-4521-a6f4-afd407a12338" />
</p>
<p>
Rename "ost-sampleconfig.php" to "ost-config.php"
<br/>
The default path is C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
<br/>
Right click "os-config.php" -> Properties -> Security tab -> Advanced -> Disable inheritance -> Remove all inherited permissions -> Add -> Select a principal -> Type "Everyone" into the 3rd box -> Check Names -> OK -> Check the box "Full control" -> OK -> Apply
</p>
<br/>

<p>
<img width="406" height="621" alt="image" src="https://github.com/user-attachments/assets/aebc3629-f59e-4214-b502-3d8c06ee8a7a" />
</p>
<p>
In the browser, go through the setup of the System Settings and create the Admin User.
</p>
<br/>

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/23adad85-a678-411e-8992-537e556e0378" />
</p>
<p>
Install <a href="https://www.heidisql.com/download.php">HeidiSQL</a>. If prompted, install for yourself only, not all users.
<br/>
Open and create a new session. The user is "root", and the password is what you set during the mySQL setup
<br/>
Right click the "Unnamed" button on the left and create a database named "osTicket"
</p>
<br/>

<p>
<img width="808" height="334" alt="image" src="https://github.com/user-attachments/assets/74d563e6-2c99-479a-9b7d-1e97c69a446e" />
</p>
<p>
Finish setting up osTicket in the browser
<br/>
The mySQL database is osTicket as set in the HeidiSQL setup, login user is "root", and the password is what was set in the mySQL setup
<br/>
Click "Install Now!"
</p>
<br/>

<p>
<img width="1917" height="1039" alt="image" src="https://github.com/user-attachments/assets/1cad9a8e-dc5e-46f3-ba77-834308d5ad01" />

</p>
<p>
Your help desk login page is at http://localhost/osTicket/scp/login.php
<br/>
</p>
<br/>

<p>
<img width="1917" height="1037" alt="image" src="https://github.com/user-attachments/assets/8cee233a-8850-4229-95d0-275075131879" />
</p>
<p>
Your end user login page is at http://localhost/osTicket/ 
<br/>
</p>
<br/>

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dc12a675-ba8f-412c-9020-613e2e8fb4b2" />
</p>
<p>
Important final steps:
<br/>
Delete: C:\inetpub\wwwroot\osTicket\setup
<br/>
Set the config file permissions to Read only at C:\inetpub\wwwroot\osTicket\include\ost-config.php
<br/>

</p>
<br/>
