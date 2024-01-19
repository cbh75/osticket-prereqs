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

Next, click the small plus (+) symbol to expand the folder. Once opened, expand the **World Wide Web Services** folder, and then do the same for **Application Development Services**. In this folder, we want to enable **CGI**.

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

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/517dc956-0d80-49f6-b412-f0782b9cdb1c)

Once the IIS Manager opens, click **Restart** on the right side of the window.

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/d619ee2f-83b1-479f-b675-117244340331)

After restarting the server, download [osTicket](https://osticket.com/download/). We will be using the latest version, which at the time of this tutorial is v1.18.1. Since this is just a basic guide, do not include any plugins.

