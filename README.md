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

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- <a href="https://github.com/osTicket/osTicket">osTicket
- <a href="https://www.php.net/">PHP
- <a href="https://www.heidisql.com">HeidiSQL (or another MySQL interface)
- <a href="https://www.mysql.com/">MySQL database
- <a href="https://www.iis.net/">HTTP server using Microsoft IIS

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
<a href="https://github.com/phpmanager/phpmanager/releases">PHP Manager for IIS (x64)
<br/>
<a href="https://www.iis.net/downloads/microsoft/url-rewrite">Rewrite Module (x64)
<br/>
<a href="https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-supported-redistributable-version">Visual C++ Redistributable
<br/>
<a href="https://dev.mysql.com/downloads/mysql/">MySQL
<br/>
Create a directory in C:\PHP and unzip <a href="https://www.php.net/downloads.php">PHP into it
</p>
<br />

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f0a4a2b3-9087-4335-912f-2191536f7eac" />
</p>
<p>
Open IIS as an Admin.
<br/>
Register PHP in the IIS. Double click "PHP Manager" -> Register new PHP version -> Path to "php-cgi" (Found where PHP was extracted. This example is in C:\PHP)
<br/>
Reload the web server by right clicking the server in the top left stopping, then starting.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In IIS on the left, click sites -> Default -> osTicket -> on the right, click "Browse *:80" to open the site.
<br/>
To enable the imap and intl extension, in IIS on the left click sites -> Default -> osTicket
<br/>
Double click PHP Manager
<br/>
Click "Enable or disable an extension". Enable "php_imap.dll" and "php_intl.dll"
<br/>
Reload the web server by right clicking the server in the top left stopping, then starting.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Rename "ost-sampleconfig.php" to "ost-config.php"
<br/>
The default path is C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
<br/>
Right click "os-config.php" -> Properties -> Security tab -> Advanced -> Disable inheritance -> Add -> Type the following name in the 3rd box "" -> Check Names -> OK -> Check the box "Full control"
</p>
<br/>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the browser, go through the setup.
</p>
<br/>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<a href="https://www.heidisql.com/download.php">Install HeidiSQL
<br/>
Open and create a new session. The user is "root", and the password is what you set during the mySQL setup
<br/>
Create a database named "osTicket"
</p>
<br/>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finish setting up osTicket in the browser
<br/>
The mySQL login user is "root", and the password is what was set in the mySQL setup
<br/>
Click "Install Now!"
</p>
<br/>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Your help desk login page is at http://localhost/osTicket/scp/login.php
<br/>
</p>
<br/>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Your end user login page is at http://localhost/osTicket/ 
<br/>
</p>
<br/>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Final steps:
<br/>
Delete: C:\inetpub\wwwroot\osTicket\setup
<br/>
Set the config file permissions to Read only at C:\inetpub\wwwroot\osTicket\include\ost-config.php
<br/>

</p>
<br/>
