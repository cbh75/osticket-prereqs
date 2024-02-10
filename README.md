<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 11</b> (22H2)

<h2>Prerequisites</h2>

- [Creating and Connecting to A Virtual Machine in Azure](https://github.com/cbh75/configure-vm)

  All of the following installed inside the virtual machine:
   - [PHP Manager 1.5.0](https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10)
   - [URL Rewrite Module 2.1 x64](https://www.iis.net/downloads/microsoft/url-rewrite)
   - [PHP For Windows](https://windows.php.net/download/)
   - [Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)
   - [MySQL 5](https://dev.mysql.com/downloads/installer/)
   - [HeidiSQL](https://www.heidisql.com/download.php)

<h2>Setting up osTicket</h2>

In your virtual machine, in the search bar, type in "control panel", and open it.

Under programs, click on **Uninstall a program**. This will bring you to a list of all currently installed programs, but that isn't what we're here for. On the left side, click on **Turn Windows features on or off**.

In the box that pops up, navigate to the folder named **Internet Information Services**, and click the box next to it to enable it.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/01a0c2bb-ac9b-4808-b267-ff59c85dde52)

Next, click the small plus (+) symbol to expand the folder. Once opened, expand the **World Wide Web Services** folder, and then do the same for **Application Development Features**. In this folder, we want to enable **CGI**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/788b7570-2412-43c3-8325-c5bcaf5ec949)

Collapse the Application Development Features folder using the minus (-) symbol. Next, expand the **Common HTTP Features** folder and enable *everything*. Once everything is enabled, collapse the Common HTTP Features folder.

Expand the **Web Management Tools** folder and ensure that **IIS Management Console** is enabled. Click **OK**. Once you see the following window, click **Close**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/50b21b24-4780-4086-bca8-77b39902e9a4)

Next, Download and install both [PHP Manager 1.5.0](https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10) and [URL Rewrite Module 2.1 x64](https://www.iis.net/downloads/microsoft/url-rewrite).

Once those are installed, open **File Explorer** and navigate to "C:\".

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/f5e76561-48b0-43b5-a28c-e94fcec26501)

In "C:\", create a folder named **PHP**. Download [PHP For Windows](https://windows.php.net/download/) and extract it into the "C:\PHP" directory we just made.

Next, download and install the [Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Once this completes, download and install [MySQL 5](https://dev.mysql.com/downloads/installer/). When prompted, choose **Server only**.

Once it finishes installing, the installer will move continue to configuration.

For **Type and Networking**, the defaults are fine.

For **Accounts and Roles**, pick a root password that will be easy for you to remember. Feel free to keep this in a safe place so you don't forget!

Everything onwards can use the defaults, so click **Next** until you get to **Execute** and then click that. Once the configuration is complete, click **Finish**.

Next, type "iis" into Windows search and run the IIS Manager as an administrator.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/d6debea8-268c-4a9a-93cb-6cec1fca5332)

Once the IIS Manager opens, navigate to **PHP Manager**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/ad2e4bb6-27ae-47ca-8fdd-d706d84051a3)

Click on **Register new PHP version**, and navigate to your php-cgi.exe file, which in our case is at **C:\PHP\php-cgi.exe**. Once you've provided the path in the text box, click **OK**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/3d64fca6-bb69-4b3d-bcd8-4c26ce3dd94a)

Click the Back button (left arrow), then click **Restart** on the right side of the window.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/1ea6fd72-608c-4df7-baba-106b59ce22d3)

After restarting the server, download [osTicket](https://osticket.com/download/). We will be using the latest version, which at the time of this tutorial is v1.18.1. Since this is just a basic guide, do not include any plugins.

When you open the osTicket zip file, you will see two files, named "scripts" and "upload". Extract and copy the "upload" folder to **C:\inetpub\wwwroot**. (This may take a couple minutes!) Once it finishes copying, simply rename the "upload" folder to "**osTicket**". Below is what the directory should look like when you are finished.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/a033cf2a-401d-43ff-8a1a-fd85bb35cb51)

Now that you have the osTicket folder, reload the IIS services once again by opening IIS Manager and clicking restart. After the server is restarted, go to the list on the left side. Click the arrow next to your machine to open a drop-down list, and then click the arrow next to **Sites**, and then click on the **osTicket** folder.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/2deb5b4a-c4e4-4eb1-8739-bd557407e3ea)

On the right side, click **Browse *:80 (http)**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/1941bca0-fab9-4cbb-818a-c0f25bb3ffc8)

If you have done everything correctly, you should see the following page:

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/119511c1-93bd-4a31-a09c-728d673d62fd)

If so, congratulations! You have succesfully installed osTicket! However, we're not quite finished yet. We need to install some extensions.

Go back to IIS Manager, making sure your "osTicket" folder is selected on the left side drop-down window. Then, go to **PHP Manager**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/e73ee9cd-b43f-4fe6-8bf3-acc67846abc6)

Click on **Enable or disable an extension**, then make sure **php_imap.dll**, **php_intl.dll**, and **php_opcache.dll** are all enabled. 

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/f3ebf88c-afee-45bf-896f-0101888a8bd3)

Once these are all enabled, refresh the osTicket page in your browser. You'll notice that some of the recommended prerequisites that were previously disabled are now enabled.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/4442c413-b1dd-4d70-a5a1-88c2927f030e)

Now we need to set up a SQL client. For this tutorial, we will use [HeidiSQL](https://www.heidisql.com/download.php). When installing, the default options are fine, so just run through the installer wizard until it finishes. Once it finishes, HeidiSQL should open automatically. If not, open it manually.

Once the window opens, click **New** to create a new session. In the new session options, make sure the user is **root** and enter the same password you chose when making the MySQL server.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/3a83d016-f5fe-44dc-a9bd-7db2c40c64fa)

Once these are filled out, click **Open**. This should take you to a screen similar to the one below.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/ddf832a4-05a5-4bd3-be61-40dc487dbf33)

At this screen, right click in the left sidebar, then go to **Create new** and then click on **Database**. Call this database "osTicket". You will see your new database added into the list.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/582d0a7e-3b62-4140-9a47-cf3abee0d1b1)

Navigate back to your osTicket setup page in your browser if it is not already there. If the steps have been followed correctly, it should be at "localhost/osTicket/setup". Alternatively, you can click on "Browse *:80 (http)" again in IIS Manager with the osTicket folder selected.

On the setup page, click **Continue** at the bottom. The next screen will tell you that your configuration file is missing, which we will resolve by renaming the sample config provided to us. To do this, navigate to "C:\inetpub\wwwroot\osTicket\include\" and rename **ost-sampleconfig.php** to **ost-config.php**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/a4f0f313-5bfb-42d8-9486-6619aa782f50)

If a window pops up saying you need to provide administrator permission, click **Continue**.

Now that we have our configuration file, we need to change some permissions. Right click on **ost-config.php** and select **Properties**. Navigate to the security tab at the top, then click on **Advanced**.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/e9568889-659d-4492-b945-34f62171c201)

In the new window, click **Change permissions**, then **Disable inheritance**. When it asks what you would like to do with the current permissions, click **Remove all inherited permissions from this object.** Next, click **Add**. In the next window, click **Select a principal** at the top, and then in the text box type "Everyone". Click **OK**, then tick the box next to "Full control". This will automatically tick the rest of the boxes. Click **OK**, then **OK** again.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/f673e243-97f9-4a64-8b8b-86d58180032b)

Once this is done, we can click **Continue** on our osTicket page. On the Basic Installation page, choose a helpdesk name and default email address to receive customer emails. You will also have to set up a primary administrator account. For the database settings, type in **osticket** for the database, **root** for the username, and enter the password you chose earlier.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/3a6256b2-47a8-468c-8fcd-24e5c6a9329f)

Once this is all entered, click **Install now** at the bottom. Give it a couple seconds, and then hopefully you will see this page:

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/773f1b48-bbcd-43bc-b9a0-1aacdc667848)

If so, congratulations! You have succesfully installed osTicket! Now all we have to do is a bit of cleanup and change our config file permissions back to read-only. To do this, navigate back to "C:\inetpub\wwwroot\osTicket\include" where our **ost_config.php** file is and open its properties again like we did earlier. Navigate to **Security**, then click **Edit**. The only group listed should be "Everyone", so at the bottom uncheck every box except for the one next to **Read**. Click **OK**, then **OK** again.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/97351823-3563-4482-878a-9a5642c62ce7)

Next, navigate back one to the osTicket folder, and delete the **setup** folder, as we no longer need it.

And with that, we are finally finished installing osTicket!

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/04ca0424-5665-4ca4-8418-8def9092ed8c)
