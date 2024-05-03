# Active-Directory-Lab
<!--[Brief Objective - Remove this afterwards] -->

The Active Directory (AD) lab aim is to provide a controlled environment for hands-on training and testing of security measures. By simulating real-world AD configurations and attack scenarios, cybersecurity professionals can hone their skills in detecting, mitigating, and preventing cyber threats. AD labs enable practitioners to experiment with security controls, policy implementations, and incident response procedures without risking production systems. The primary focus was understanding attack vectors, conducting red team vs. blue team exercises, and ensuring compliance with security standards. Ultimately, this hands-on experience has provided me with an indepth understanding of cybersecurity and how to mitigate evolving threats.

### Skills Learned
<!--[Bullet Points - Remove this afterwards] -->

- Gained a deep understanding of Active Directory components, such as domains, forests, organizational units (OUs), users, groups, and group policies.
- Proficiency in analyzing and interpreting network logs.
- Learn networking concepts, including IP addressing, subnetting, routing, and DNS configuration, to set up the network infrastructure.
- Ability to generate and recognize attack signatures and patterns.
- Cultivate documentation skills to record the configuration details, settings, and procedures followed in building and managing the AD lab, which can serve as a reference for future use and troubleshooting.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used
<!--[Bullet Points - Remove this afterwards] -->

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Network analysis tools (Sysmon) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps

## Active Directory Project (Home Lab) | Intro
What is Active Directory?

Active Directory (AD) is a service provided by Microsoft for managing resources in a networked environment. It's like a central nervous system for an organization's IT infrastructure. Here's a simpler breakdown:

Think of a school. In that school, you have students, teachers, classes, and maybe even different departments like math or science. Now, imagine keeping track of all the students, teachers, classes, and departments in one big book. That's what Active Directory does, but for computers, users, printers, and other resources in a company or organization.

What we well be doing in this Lab:

Build a diagram to display my project

Install virtual machines - Windows 10, windows Server, Kali Linux, and Splunk. This will be done by using virtual box.

install and configure Software. Sysmon which will be used for logging purposes and Splunk which will be used to query for telemetry. 

Configure Active Directory on a windows server and how to promote it to a domain controller I also created new domain users to log into the newly created domain and I also joined the targeted pc into the domain

Generate telemetry with Kali Linux and Art(Atomic red team).

## Active Directory Project (Home Lab) Part 1

In this part I going to focusing on Creating a logical diagram to showcase what I’ll be doing, along with the hardware requirements. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/fca7b92f-f39e-4d1e-ab1d-5b2faecbb499)

All devices are on the same network 192.168.10.0/24 with a Subnet Mask of 255.255.255.0   

Server 1 is my Splunk server which is going to neatly organize my huge amount of data so that i can easily search for specific things

Server 2 is going to be my Active Directory that store all my information like, Centralized management, User Authentication and Authorization, Group Policies and Directory Services. A brief explanation for each is below

Centralized Management: stores information about all the computers, users, printers, and other devices on a network in one place. This makes it easy for me to manage and organize everything from a single location.

User Authentication and Authorization: When someone tries to log in to their computer or access a file, Active Directory checks their username and password to make sure they're allowed to do so. It also determines what level of access they have based on their role or group membership.

Group Policies: Allows me to set policies and rules for users and computers. For example, I can enforce security settings, install software on all computers in a certain department, or restrict access to certain files or folders.

Directory Services: This provides a directory service, which is like a phone book for all the resources on the network. It makes it easy to find and access printers, files, and other resources without having to know their exact location.

Server 2 also have a Splunk Universal forwarder to send information to the Splunk Server which the Sysmon collected.

 My windows 10 machine is going to be assigned its IP through DHCP and also had Splunk Universal forwarder installed to facilitate the forwarding data to the Splunk server 

My red PC is the attacker.

And of course we have the internet in the green cloud.

## Active Directory Project (Home Lab) | Part 2

Installing Virtual Machines 

Windows 10

Kali Linux

Ubuntu Server 

Windows Server 2022

Virtual Box

Virtual Box installation 

step 1.  Downloading virtual box

Go to Virtualbox.org click download.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/a8d7d762-df5e-431f-8d8a-d0e6e023181c)

step 2. Verifying the integrity of downloaded packages.

click “SHA”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/6ea27f1a-5189-4f20-8dd3-fcb216c7be82)

then it will take you to this page below

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/23835189-44b9-4fcf-bbfd-e9d7c70680ac)

step 3. Navigate to your downloads folder and then right click to open your terminal 



![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/3d82e2d2-e41d-4816-8421-376689211fbd)

step 4. In your terminal you type the follow commands.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/32323428-1dac-435a-97bc-2e87f5dc43a0)

Then compare the hashes you received from step 2.

Step 4. Click your virtual box download and follow the instructions. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/8e75c89a-1c1a-42b2-8448-af8057c4787d)

Installing Windows 10

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/86e46aaf-5c74-475d-b79b-f3b5fa977050)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/efc49293-93da-4aaf-b475-53bf800a5219)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/46780379-164f-4f7a-a4a5-9037ee498e8c)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/69a172c9-e43c-4ab4-b7d2-4d48cbdd3646)

After you finished downloaded click ‘finish’. 

Then you can go ahead and install windows 10 into your virtual box.

Installing Windows 10 into Virtual Box

Open virtual box and click “New”

Screenshot 2024-04-23 224127.png
Enter a “Name”:

Then Enter the Iso Image by clicking the arrow and selecting “other”, navigate to the downloaded file. 

Screenshot 2024-04-23 224328.png
Next page.

Screenshot 2024-04-23 224428.png
Next page. 

Screenshot 2024-04-23 224533.png
Next page. 

Screenshot 2024-04-23 224614.png
Next page. 

Screenshot 2024-04-23 224708.png
Then click the start button and finish installing Windows 10.

Screenshot 2024-04-23 224857.png
Then click “Install”.

Then click “I don’t have a product key”

Screenshot 2024-04-23 225020.png
Then click “Windows 10 pro”

Screenshot 2024-04-23 225125.png
Then accept the agreements.

Then click “Custom Install Windows only (advanced)”

Screenshot 2024-04-23 225444.png


Screenshot 2024-04-23 225547.png
Click “Next”

Next Page, wait for the installations 

Screenshot 2024-04-23 225655.png
Installing Kali Linux

Screenshot 2024-04-23 225927.png
Click Download.

Navigate to “Pre-built VMS”

Ensure your system is compatible  with download.

Screenshot 2024-04-23 230256.png
Install VirtualBox 64 2.96G

Next step is to navigate to “7-zip.org” website to unzip your kali download. 

Screenshot 2024-04-23 230730.png
Click “Download | exe | 64-bit x64 | 1.5 MB” then install 7zip

Navigate to your downloads and install Kali Linux 

Screenshot 2024-04-23 232627.png
After the process is finished Open your new Kali Linux

Screenshot 2024-04-23 232935.png
Double Click Kali-Linux.

Screenshot 2024-04-23 233018.png
Install Kali in Virtual box. 

Installing Windows Server

Navigate to google and search for “window server 2022 iso” then click “download the iso”

Screenshot 2024-04-24 003931-20240424-043931.png
Then fill out the questionnaire.

Next page click on “64-bit edition”

Screenshot 2024-04-24 004058.png
After finish downloading add the file to your virtual box follow steps from above.

The Windows server Installation below.

Click “start” Then wait for windows server to boot up the hit “next”

Screenshot 2024-04-24 005131.png
Then click “install”.

The click second option because it gives a more user friendly GUI.

Screenshot 2024-04-24 005316.png
Then accept terms and agreements.

The next page select “Custom”.

Then click “Next”

Microsoft Server will take its time to start up.

Installing Splunk Server 

Navigate to Ubuntu.com 

Click “Products”

Screenshot 2024-04-24 011725-20240424-051726.png
Next page.

Screenshot 2024-04-24 011743-20240424-051743.png
Next page is too choose the latest version of ubuntu server.

Then navigate to virtual box to install. Follow steps for installation below. 

Click “new”

Then give Server a “name”, then add ISO Image from download folder by click “other” 



Screenshot 2024-04-24 014622.png


Set memory to 8GB and processor to 2 

Screenshot 2024-04-24 014657.png
Set to 100GB

Screenshot 2024-04-24 014710.png
After completed click “Start” to power on server

Follow instructions below to set up

For the first few steps click “enter”  

Screenshot 2024-04-24 015033.png


Then click “continue” when prompted

Screenshot 2024-04-24 015135.png
Click “done” for next few prompts.

Then click “continue” 



Screenshot 2024-04-24 015338-20240424-055339.png
Then enter credentials. 



Screenshot 2024-04-24 015456.png
After click “done” for next few steps.

Then wait for installations until you see “reboot now”

Click “reboot now”

When prompted with page below hit “enter”

Then log into server. 

Don’t worry about not seeing password, type correct password and then click Enter.

The run an upgrade on server using command below. 

## Active Directory Project (Home Lab) | Part 3

Objective:

Install & Configure both Sysmon & Splunk onto our Windows target machine and the Windows Server so that they can start collecting telemetry and send logs over to our Splunk Server.

To start make sure that the network settings are set to “NAT Network” on virtual box 

so that the virtual machines can be on the same network and still have internet access.

Instructions are as follows.

Navigate to virtual box, click “tools” the “network”

Screenshot 2024-04-26 132744.png


Click “NAT Network” then click “Create”

Down at the bottom of the page change to whatever is suitable “Name” as for “IPv4 Prefix” refer back to diagram, when finish make sure to hit apply.

Next is to change Splunk network settings to “Nat Network” refer to diagram below.

click “Splunk” then “settings” then “network”. In Adapter 1 change “Attached to” to the network created previously, then change “Name” to the name you specified, then click “OK”



Screenshot 2024-04-26 134227.png
Next is to do the same for all virtual machines downloaded in this project.

After doing so the next step is to check Ip address on Splunk server to match Ip specified in the diagram I created earlier and if it doesn’t match I have to change it.

To change or resetting IP address which is setting up a Static IP address.

Instructions: 

note. “sudo nano /etc/netplan/” Click “Tab” on keyboard to auto complete.

When prompted with the next page enter in the information from the diagram created in part 1. Example is below, Use “Tab” and arrows to navigate. When finish “Ctrl + x” to save then type “y”. clear screen after



Next Step is to apply changes. When prompted with warnings, ignore because we are just a “LAB” environment.

Screenshot 2024-04-26 140817.png
  After doing so retype “ip a” in command line to check if changes have been made to IP address.

Also check connection with “ping google.com” . If didn’t work redo steps above.

note: “Ctrl c” to stop ping.

Next is start installing Splunk if all connection works. Note: install Splunk on your PC not virtual machine. 

Navigate to “Splunk.com”

Screenshot 2024-04-26 141537.png
 Make sure to sign if haven’t already.

When finish click “Products” then “Free Trails & Downloads”

Screenshot 2024-04-26 141723.png
Scroll down to “Splunk Enterprise” click “Get My Free Trail” 

Next. select “Linux” then download the “.deb” . Save file in a directory of your choice.

Screenshot 2024-04-26 141947.png
Navigate back to Splunk virtual box and Install the guest add-ons for virtual box.

Note: “Tab” was use to identify options and also to auto complete.

Click enter and when prompted type “y” then click “Enter” it may take a while to download. when prompted with screen below hit “Enter” then clear screen 

 When cleared in the top left corner click “Devices” then “Shared Folders” then “Shared Folder Settings”

Screenshot 2024-04-26 142847.png
Add folder.

Screenshot 2024-04-26 142943.png
For the “Folder Path” Select the folder where the Splunk installer was downloaded to, an example is below.

Click “OK” when done.

Screenshot 2024-04-26 151214.png
Back on Splunk command line Type “sudo reboot”

Log back in when prompted.

Then when logged in Add user to the vbox SF group.

Note: User name might be different.

Screenshot 2024-04-26 151543.png
If this pops up install additional guest requirements. Click “Enter” when done. 

Screenshot 2024-04-26 151903.png
Then “sudo reboot”

Log back in.

Try again and add user to that group

Note: User name might be different for you

Next step is to create a new directory called share.

 Now that new directory has been created, mount shared folder onto the directory called share  

folder name created earlier was: 

Then click “Enter”.

Next steps are shown.

The next imagine shows all files listed in the Directory, Including the Splunk Installer.

Installing Splunk. Then wait until its “complete”.

Screenshot 2024-04-26 153234.png
Next step is to change into the directory where Splunk is located onto our server.

Note: All the “Splunk Splunk” is good because it limits the permission to that user.

Screenshot 2024-04-26 154117.png
Change into the user name Splunk.

Then “cd” into “bin”. The files listed in here are all the binary splunk can use.

Next step. 

When prompted with the license agreement click “q”

then type in “y”

Follow instructions when prompted.

Everything should be installed.

For extra measure. Enter the following command so that splunk start up every time the virtual machine reboots

Installing Splunk Universal Forwarder and Sysmon on the target machine and server.

   Optional step. 

Changing the name of the target machine to Target-PC

Next is to make sure the IP address matches our diagram.

If IP address doesn’t match it would have to be changed.

Then right “Ethernet”

Then click “Properties” 

Next is to double click on “Internet Protocol Version 4”



Fill in the fields.

Then click “OK”

Navigate back to Command prompt and enter “ipconfig” the IP address should be changed

Screenshot 2024-04-26 214437.png
Click on the browser and  try to access Splunk server. Splunk listen on port 8000

Screenshot 2024-04-26 214603.png
should be prompted with the page below

Screenshot 2024-04-26 214617.png
If you run into a problem which I did, navigate to back to the Splunk server and type the follow command to make sure the server is listening. 

Screenshot 2024-04-26 215219.png
Screenshot 2024-04-26 215238.png
Then navigate back to the target PC and try to reconnect to the Splunk server.

Next step is to install Splunk Universal Forwarder. Head to Splunk website on the Target Pc and login with the account you created earlier.

Screenshot 2024-04-26 220303.png
Screenshot 2024-04-26 220322.png
Head to the download folder and install Splunk Forward.

Follow instruction below. 

Installing Sysmon. Follow instruction below.



Sysmon Configuration. Follow instruction below

Scroll all the way down.

Screenshot 2024-04-26 221538.png
Then click on “Raw” on the right hand side.

Screenshot 2024-04-26 221637.png
Next right click “Save as”

Save it under the downloads directory

Screenshot 2024-04-26 221807.png
Navigate back to downloads folder and extract Sysmon file.

Click Extract.

Then right click on “Copy”

Next open PowerShell and run as administrator. 

On the command line change directory and paste the what was copied before.

Then type “Sys” hit tab until you see .\Sysmon64.exe. See more below

Next step is to instruction Splunk Forwarder to send what we want over to the Splunk Server. Instruction are below.

The image below is Instructing the Splunk Forwarder to push events related to application, security and system as well as Sysmon over to the Splunk server

 

Save note pad file under This pc > Program Files > Splunk Forwarder > etc > System > local.

Change file name to “input.conf” 

Change Save as Type to “All Files”

click save. 

Next is to restart Splunk’s Universal Forwarder Services. Instructions are below.

Screenshot 2024-04-26 225839.png
Screenshot 2024-04-26 225903.png


Screenshot 2024-04-26 225919.png
Now we have Sysmon install and Splunk Universal Forwarder along with the updated inputs.conf file.

Now head over to the Splunk Server login page and sign in with your credentials. 

When inside Click “settings” at the top then click on “Indexes”

Create a new index call “Endpoint” 

click “save”

Next is to make sure our Splunk server to receive the data.

Navigate to settings > Forwarding and receiving then under “Receiving data” click on “Configuring receiving” next click on “New Receiving Port”. 

Click on Apps > Search & Reporting 

We have successfully install and configured Sysmon and Splunk.

Next is to setup the Windows Server, It is the same way to setup so follow the steps in pervious explained.

When finish the Splunk Server should have something like this. 

## Active Directory Project (Home Lab) | Part 4

objectives 

install and configure active directory on to the server then promote it to a domain controller 

Configure the target PC to join the newly created domain 

First navigate to the windows server on virtual box open your server and check to make sure the IP address is set to 192.168.10.7 subnet mask 255.255.255.0 Default gateway 192.168.10.1. In pervious steps we had already configured this information.

Test connectivity to make sure everything is working.

Screenshot 2024-04-30 133735.png
Once everything is working head over to Server Manager which is the icon you see below

Screenshot 2024-04-30 133905.png
Follow instructions to configure Server manager. 

Screenshot 2024-04-30 134017.png
Click “Next”

Click “Next”

The following page select “Active Directory Domain Services” then Click on “Add Features”

Click “Next” a few more times until you reach the “Installation progress” wait until installation is done 

when done “close” it out.

Click the Flag icon at the top then select “Promote the server to a domain controller 

Next page select “Add a new forest” then enter a Root Domain name. Make sure the domain name (.something) for example mydir.local or hello.goodbye. Click Next when finish 

Enter a password.

Click “Next” a couple times. 

The page below is shows the important folders. Attackers love to target domain controller.

Continue click “Next” until this page below pops up

Screenshot 2024-04-30 140230.png
The click “Install” 

When the process is completed the server will ask to reboot. Click reboot

The log back into the Server. 

If you get a back”\” like that you everything was done good.

Screenshot 2024-04-30 140814.png
Next step is to create users. 

When logged back in your server navigate back to Server Manager and click on “Tools” > “Active Directory Computers”

This is where we can create objects such as users computers, groups and many more.

Expand mydfir.local

Right click on mydir.local



image-20240430-233411.png
Then click finish.

A new user in IT called jenny is created. 

Creating HR Department 



Then Click “Finish”

Next is to head over to the Target-Pc and join it to the newly created domain called mydfir.local and then authenticate using Jenny smith account. 



On the windows 10 Pc/Target-PC Type “pc” then click on properties

image-20240430-235230.png
Scroll down to “Advanced system setting”

image-20240430-235303.png
To fix this Error Navigate to “Network Adapter” 

image-20240430-235638.png
image-20240430-235653.png
Double click on “IPV4”

Change Preferred DNS Server to the IP address to the windows server. 192.168.10.7 the click “OK” a couple times 

To check configurations have been made navigate to Cmd command prompt 

image-20240501-000138.png
Go back to the pervious configurations and click “OK” and it should work.

image-20240501-000259.png
The you should be prompted to enter some credentials to login. Use the administration of the server to login

image-20240501-000456.png
Next prompt should ask to restart device.

image-20240501-000603.png
Click “close” then click “restart now”

image-20240501-000652.png
When present with the screen below, change the login information to jenny smith.



Enter Jenny Smith credentials 

image-20240501-000911.png
That’s how to create new users, join computers to a new domain and log in as a domain user.

## Active Directory Project (Home Lab) | Part 5

objectives 

Use Kali Linux to perform a brute force attack.

Viewing Telemetry via Splunk

Setup & Install ART(Atomic Red Team) and run test.






*Ref 1: Network Diagram*
