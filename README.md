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

- Microsoft Azure account (this could be done in other cloud providers, but this tutorial uses Azure)

<br />

<h2>Creating the Virtual Machine</h2>

Go to the Azure portal and go to your virtual machines. The easiest way to do this is to locate the search bar at the top of the page and simply type in "virtual machines".

<br />

![1](https://github.com/cbh75/osticket-prereqs/assets/62080815/1c9898b8-14cf-42ff-8322-9586a87f2ba5)

<br />

After clicking on **Virtual Machines** in the search bar, you will be taken to your Virtual Machines page listing all of your VMs. You probably won't have any right now, so click on **Create** in the top left corner. This will produce a drop-down box with the different types of VMs you can create. For this tutorial, we will use the first option, **Azure virtual machine**.

<br />

![2](https://github.com/cbh75/osticket-prereqs/assets/62080815/1cb56175-eceb-480e-9c5a-24c006139e86)

<br />

<p>On the next page, scroll down to <b>Instance Details</b>. <br />
For the virtual machine name, you can call it whatever you want, but for simplicity sake we'll call it <b>vm-osTicket</b>. <br />
For image, select <b>Windows 11</b>. <br />
The size of the machine doesn't matter too much, but you generally want <b>4 GB</b> of RAM or larger.</p>

<p>Next, scroll down to <b>Administrator Account</b>. Pick any username you want, along with a password.<br />
<b>Make sure you remember these!</b></p>

<br />

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/e676cd14-d74a-47a8-b4ef-3f80bda23249)
![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/537c0c69-e917-4773-acf4-c33186ad4cbe)

<br />

<p>Next, scroll to the bottom . Under <b>Licensing</b>, check the box confirming you have an eligible Windows license. After the box is checked, click on <b>Review + create</b>.</p>

<br />

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/c0eec9ea-f956-431c-88cb-acd6033d97a8)

<br />

<p>Azure will attempt to validate the VM. Once validation has passed, click the button at the bottom that says <b>Create</b>.</p>

<p>After giving Azure some time to deploy the VM, you should see a green check with some text saying "Your deployment is complete".</p>

<br />

![7](https://github.com/cbh75/osticket-prereqs/assets/62080815/8d8a31be-bf81-430a-9de4-008f18841873)

<br />

<p>Congratulations, your virtual machine has been created!</p>

<br />

<h2>Connecting to the Virtual Machine</h2>

<p>Go to the search bar in Windows and type in "remote desktop connection".</p>

<br />

![1](https://github.com/cbh75/osticket-prereqs/assets/62080815/64bc4f73-a2ad-4ff3-9b42-f351c045bb52)

<br />

<p>Click on the Remote Desktop Connection application. The window for Remote Desktop Connection will appear, but minimize it for now.</p>

<p>Go back to the Azure portal, and navigate to your virtual machines using the same steps we did in the previous section. You should see the VM we created in the previous section, <b>vm-osTicket</b>.</p>

<br />

![2](https://github.com/cbh75/osticket-prereqs/assets/62080815/c5ff3302-1c96-4d86-ab98-3469f4545196)

<br />

<p>After clicking on our VM, we are taken to a page displaying all the information about our VM. In this case, we are looking for the <b>Public IP address</b>.</p>

<br />

![3](https://github.com/cbh75/osticket-prereqs/assets/62080815/0b0d7b70-c3fc-4494-ab13-c367a1edb5e9)

<br />

<p>Copy this address, and then go back to the Remote Desktop Connection window. In the <b>Computer</b> text box, paste the IP address. </p>

<br />

![4](https://github.com/cbh75/osticket-prereqs/assets/62080815/6b9e7ecd-0043-473d-b753-65868e9aec17)

<br />

<p>Click <b>Connect</b>. A Windows Security window will pop up asking you to enter your credentials. At the bottom, click on <b>More choices</b> in blue text. Then click <b>Use a different account</b>. This will allow you to type in the username and password you chose when creating the virtual machine.</p>

<br />

![5](https://github.com/cbh75/osticket-prereqs/assets/62080815/874632ae-7dbf-40eb-add4-889c90c49aca)
![6](https://github.com/cbh75/osticket-prereqs/assets/62080815/2204a025-8fc4-4d91-b6fa-d34fc85d329e)

<br />

<p>Click <b>OK</b>. Before it attempts to connect, An additional window will pop up informing you that the identity of the remote computer cannot be verified. Click <b>Yes</b>, and then we will be connected to the VM.</p>

<p>Once connected, wait for your user to sign in. This may take a while, depending on the size you chose when setting up the virtual machine. Once signed in, go through the Windows setup. When you are finished, you will be greeted with the desktop. To ensure you are connected, look for a blue bar at the top of your screen. This indicates that you are controlling the virtual machine.</p>

<br />

![image](https://github.com/cbh75/osticket-prereqs/assets/62080815/64e1bc59-47f5-44a7-8023-53acc60d10c5)

<br />

<p>If you see this, congratulations! You are connected to your virtual machine!</p>
