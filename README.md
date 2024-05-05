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

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/d7b68996-8cdd-430c-bec0-d3b303c189d0)

Enter a “Name”:

Then Enter the Iso Image by clicking the arrow and selecting “other”, navigate to the downloaded file. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/3865e149-f18a-4a71-ab22-9995430357a3)

Next page.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/0a80a406-ba9e-46a8-bc6a-753f3a54750b)

Next page. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/8e0602c4-23b9-497e-9f3e-9b9c27ce19ec)

Next page. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b7c2c225-5e63-44dd-b649-da7957ef2cb0)

Next page. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/7492a541-e398-4b64-878b-9461910a2f3c)

Then click the start button and finish installing Windows 10.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/7067a1bd-275a-4761-9fb7-abd50977e92a)

Then click “Install”.

Then click “I don’t have a product key”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/25c0f1aa-9fde-49a0-8822-901dbc2dffba)

Then click “Windows 10 pro”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b0071dbc-e1d5-482e-8031-dd6023405ccc)

Then accept the agreements.

Then click “Custom Install Windows only (advanced)”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/2f5223a1-2f8f-46b6-8160-ebeb1d5b9303)



![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/d941227e-395b-4332-9d89-a18105154075)

Click “Next”

Next Page, wait for the installations 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/186de803-7bd9-47c4-8554-d96cb40508b1)

Installing Kali Linux

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b60c7f77-cf70-4f4b-ab57-38b948ae32c4)

Click Download.

Navigate to “Pre-built VMS”

Ensure your system is compatible  with download.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/eff8c892-cc2e-4106-99ae-1bcea6b31677)

Install VirtualBox 64 2.96G

Next step is to navigate to “7-zip.org” website to unzip your kali download. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/c0ca8ab0-ee3f-432c-b7a3-21701c33e7c1)

Click “Download | exe | 64-bit x64 | 1.5 MB” then install 7zip

Navigate to your downloads and install Kali Linux 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/f792433e-f184-4f82-be71-8fdeacec31a5)

After the process is finished Open your new Kali Linux

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/789a328c-9287-4baa-997c-5433bd4f8d6a)

Double Click Kali-Linux.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/ce0ca098-ef7b-40a8-8d09-f7b0648aba2b)

Install Kali in Virtual box. 

Installing Windows Server

Navigate to google and search for “window server 2022 iso” then click “download the iso”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/3d7ddb59-9f67-422f-baa0-f06cf754a150)

Then fill out the questionnaire.

Next page click on “64-bit edition”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/7beb1ae0-8537-4f5c-a971-22c32e22b6ba)

After finish downloading add the file to your virtual box follow steps from above.

The Windows server Installation below.

Click “start” Then wait for windows server to boot up the hit “next”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/bfbef4c1-1433-4c27-87ed-17ed322841d4)

Then click “install”.

The click second option because it gives a more user friendly GUI.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/fbd518b8-29dc-4f49-b905-6a8da4d7068a)

Then accept terms and agreements.

The next page select “Custom”.

Then click “Next”

Microsoft Server will take its time to start up.

Installing Splunk Server 

Navigate to Ubuntu.com 

Click “Products”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/1c13f93c-7ce0-43f3-8586-65942ec8fdb3)

Next page.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/f725a9b0-654e-4d6f-bf4a-03703c4a597f)

Next page is too choose the latest version of ubuntu server.

Then navigate to virtual box to install. Follow steps for installation below. 

Click “new”

Then give Server a “name”, then add ISO Image from download folder by click “other” 



![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/2d77c7c9-aad5-4b0b-8c79-0071e23e2fe5)



Set memory to 8GB and processor to 2 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/d3d088ef-f935-40a2-973f-d92d806d3778)

Set to 100GB

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/c306abc2-e42c-4109-8b9d-863c5d0aaec7)

After completed click “Start” to power on server

Follow instructions below to set up

For the first few steps click “enter”  

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/45225461-aace-4308-92c7-9cdd41538ad3)



Then click “continue” when prompted

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/9677a134-1caf-48bd-8e38-359a7f0daf7d)

Click “done” for next few prompts.

Then click “continue” 



![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/51e200d8-1022-4fe4-9a29-b3c111d11031)

Then enter credentials. 



![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/2900bd24-0a99-4147-b05b-993d0d962dcd)

After click “done” for next few steps.

Then wait for installations until you see “reboot now”

Click “reboot now”

When prompted with page below hit “enter”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/f51fe99d-ffc0-40ad-b2c8-18a989ce3c63)


Then log into server. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/2ff1223e-eb22-4dc0-a127-715e7251ed26)


Don’t worry about not seeing password, type correct password and then click Enter.

The run an upgrade on server using command below. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/bb64bec1-5d9d-4bba-b161-400c7162376f)


## Active Directory Project (Home Lab) | Part 3

Objective:

Install & Configure both Sysmon & Splunk onto our Windows target machine and the Windows Server so that they can start collecting telemetry and send logs over to our Splunk Server.

To start make sure that the network settings are set to “NAT Network” on virtual box 

so that the virtual machines can be on the same network and still have internet access.

Instructions are as follows.

Navigate to virtual box, click “tools” the “network”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/c4e44d2b-7a0a-43b8-82f4-f21e3779503c)


Click “NAT Network” then click “Create”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/496a2c33-6c75-4f73-8a74-6ba950b26be4)


Down at the bottom of the page change to whatever is suitable “Name” as for “IPv4 Prefix” refer back to diagram, when finish make sure to hit apply.

Next is to change Splunk network settings to “Nat Network” refer to diagram below.

click “Splunk” then “settings” then “network”. In Adapter 1 change “Attached to” to the network created previously, then change “Name” to the name you specified, then click “OK”



![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/c84a0ef7-a855-42f1-ab46-74fa5a030c52)

Next is to do the same for all virtual machines downloaded in this project.

After doing so the next step is to check Ip address on Splunk server to match Ip specified in the diagram I created earlier and if it doesn’t match I have to change it.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/a9ac5f65-50ab-4f2f-b976-e3d45a2b681a)


To change or resetting IP address which is setting up a Static IP address.

Instructions: 

note. “sudo nano /etc/netplan/” Click “Tab” on keyboard to auto complete.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/ed022d44-42f7-42e3-bb5b-6b6043514bfb)


When prompted with the next page enter in the information from the diagram created in part 1. Example is below, Use “Tab” and arrows to navigate. When finish “Ctrl + x” to save then type “y”. clear screen after

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/392c2f73-7a6c-4013-ae28-6f02f2c65966)


Next Step is to apply changes. When prompted with warnings, ignore because we are just a “LAB” environment.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b595e73a-fc9d-47ae-bc7b-95161478e7ed)

After doing so retype “ip a” in command line to check if changes have been made to IP address.

Also check connection with “ping google.com” . If didn’t work redo steps above.

note: “Ctrl c” to stop ping.

Next is start installing Splunk if all connection works. Note: install Splunk on your PC not virtual machine. 

Navigate to “Splunk.com”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/9938de5b-02d6-4469-895b-806a58d977a1)

 Make sure to sign if haven’t already.

When finish click “Products” then “Free Trails & Downloads”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/ac801f6d-b995-4b22-b98d-944658cf88ce)

Scroll down to “Splunk Enterprise” click “Get My Free Trail” 

Next. select “Linux” then download the “.deb” . Save file in a directory of your choice.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/0329233d-558e-454e-9420-4ab9281f73a4)

Navigate back to Splunk virtual box and Install the guest add-ons for virtual box.

Note: “Tab” was use to identify options and also to auto complete.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/3b9f5fb9-7826-4e84-85dc-ee95bff0b5d7)


Click enter and when prompted type “y” then click “Enter” it may take a while to download. when prompted with screen below hit “Enter” then clear screen 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/2cdc161f-1150-4a12-aa1c-99685b7089f8)

 When cleared in the top left corner click “Devices” then “Shared Folders” then “Shared Folder Settings”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/a682106c-11a4-4473-882a-682574eac6df)


Add folder.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/4d48ad0d-a945-40dd-a335-b19b77f04df9)


For the “Folder Path” Select the folder where the Splunk installer was downloaded to, an example is below.

Click “OK” when done.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/64dceeb4-baec-4ed1-9442-ae69ebac7276)


Back on Splunk command line Type “sudo reboot”

Log back in when prompted.

Then when logged in Add user to the vbox SF group.

Note: User name might be different.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/af277e50-05cd-4880-96dd-3375b8980281)


If this pops up install additional guest requirements. Click “Enter” when done. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b76c5229-dcf4-42f1-9505-3e783138771d)

Then “sudo reboot”

Log back in.

Try again and add user to that group

Note: User name might be different for you

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b9d99333-b7cf-4549-b54b-59096fec184e)


Next step is to create a new directory called share.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/274e4102-2f1b-4a27-b07f-0035e07c14ad)


 Now that new directory has been created, mount shared folder onto the directory called share  

folder name created earlier was: 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/431ef954-ce56-47cd-8660-042410fc8745)


Then click “Enter”.

Next steps are shown.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/ad920265-7d07-47b2-b748-036325ac8026)


The next imagine shows all files listed in the Directory, Including the Splunk Installer.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/5d66edc4-1183-4da6-91ba-e1e5732d30a5)


Installing Splunk. Then wait until its “complete”.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/203be7fc-41b2-49d0-84cf-4a5efdbec337)

Next step is to change into the directory where Splunk is located onto our server.

Note: All the “Splunk Splunk” is good because it limits the permission to that user.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/bcf2d668-1295-4231-a553-aceacf449e6d)

Change into the user name Splunk.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/efb121e5-b67e-4c18-8b18-28c9e42d3d13)


Then “cd” into “bin”. The files listed in here are all the binary splunk can use.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/84b6e150-d5cf-4682-b81d-444844512372)


Next step. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/d70615f9-fa06-4041-a695-3332fd0ea365)


When prompted with the license agreement click “q”

then type in “y”

Follow instructions when prompted.

Everything should be installed.

For extra measure. Enter the following command so that splunk start up every time the virtual machine reboots

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/43db5231-52c0-4dfd-adfb-cb4e8ab3f985)


Installing Splunk Universal Forwarder and Sysmon on the target machine and server.

Optional step. 

Changing the name of the target machine to Target-PC

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/2e4bdd2b-a8d8-4a11-ac52-811e6613bca9)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b22d31fc-19d3-4685-b95c-d72eb486420e)


Next is to make sure the IP address matches our diagram.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/e1ebebbc-5111-47f6-809d-4a898d309908)


If IP address doesn’t match it would have to be changed.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/1b1b55ee-5ab9-46aa-b9ae-f927fdc33bea)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/a251003c-ab58-4328-b245-aba897677a1c)


Then right “Ethernet”

Then click “Properties” 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/b88b3db5-bfae-4d4e-a953-50467f1e9cde)


Next is to double click on “Internet Protocol Version 4”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/0b7d6071-0d46-45d1-bd16-30fafc8b6187)


Fill in the fields.

Then click “OK”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/f20fdefd-70ad-4492-a060-835ea661c1f6)


Navigate back to Command prompt and enter “ipconfig” the IP address should be changed

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/4bea524a-f501-4c1e-8123-1ce41289f398)

Click on the browser and  try to access Splunk server. Splunk listen on port 8000

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/6a11ce9a-1d5a-4cc5-9418-776137d65c7c)

should be prompted with the page below

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/ec33bdd2-c96a-41ec-a257-8e2f43b59c39)

If you run into a problem which I did, navigate to back to the Splunk server and type the follow command to make sure the server is listening. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/e3cfde8a-2b82-4cd9-853b-ccf4b445bde8)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/98592400-925e-4369-b69a-f12dfab9fc49)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/45cb9fad-f22b-4958-9044-c96ee1ffd02f)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/ed85a3e5-5111-4fb0-af5c-6573e8200aa1)


Then navigate back to the target PC and try to reconnect to the Splunk server.

Next step is to install Splunk Universal Forwarder. Head to Splunk website on the Target Pc and login with the account you created earlier.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/21a71e0d-2c3c-45ab-a4c4-07cab716024f)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/31d604c8-09e2-4d2c-953f-361c6fd7fc55)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/0346e02d-6fc9-4591-8845-a84957b02dac)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/5bc0002d-c1b9-4d0e-bdb5-19414a2d8015)



Head to the download folder and install Splunk Forward.

Follow instruction below. 

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/460230ef-f39d-465b-88dd-3c406a125e80)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/93904ac1-8e25-4134-85fb-ca1ab412d4e6)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/11e0092a-67fe-43f1-9752-c92a2059cf92)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/59aa8ed3-bc6f-4a0c-9acb-5ef47a591455)


Installing Sysmon. Follow instruction below.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/97895102-eaf7-4c2e-b6d4-df8ea26ce013)

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/a2089a44-8923-42b7-90a9-11320612912c)


Sysmon Configuration. Follow instruction below

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/90f06803-0c25-4f7b-8b4a-d1ff279f5c0a)

Scroll all the way down.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/94709ff9-088c-4336-9147-15740df2fcf5)

Then click on “Raw” on the right hand side.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/97958bb9-c069-4ab2-b9d9-8d1447b91e2e)


Next right click “Save as”

Save it under the downloads directory

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/94445ace-0bcf-463c-b8ba-da85aca552b8)

Navigate back to downloads folder and extract Sysmon file.

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/a805db9c-37d4-469f-b21b-cdb035a3d464)


Click Extract.

Then right click on “Copy”

![image](https://github.com/3RR0b0t/Active-Directory-Lab/assets/168855597/4ff36ef8-41ad-4a35-bf42-f394c0809980)


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
