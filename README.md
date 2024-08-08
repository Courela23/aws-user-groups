# Utilizing Linux Command Lines to Install a Wazuh SIEM
<h2> Basic Prerequisites</h2>
  
- Install Oracle VirtualBox Download and install VirtualBox from VirtualBox's official site.
- Download Linux ISO Download the ISO file of your preferred Linux distribution from its official website.
- Create a New Virtual Machine Open VirtualBox, click "New", and follow the wizard to name your VM, select Linux as the type, allocate memory (2 GB recommended), and create a virtual hard disk (20 GB or more).
- Configure the Virtual Machine Go to VM "Settings": Adjust system settings, attach the Linux ISO under "Storage", and configure the network settings.
- Install Linux and Complete Setup Start the VM, boot from the ISO, follow the installation steps for the Linux distribution, remove the ISO, and restart the VM.
- Optional: Install VirtualBox Guest Additions for enhanced performance.

  ![Screen Shot 2023-10-25 at 4 38 51 PM](https://github.com/Courela23/aws-user-groups/assets/136120929/72bdc180-e2eb-4cb1-b260-64eb7779d305) </h1>



<h2>Environments and Technologies Used</h2>
  -A Cloud Guru.
<h1>Project Overview</h1>
The project involves AWS Identity and Access Management (IAM), a service designed for AWS customers to effectively oversee user access and permissions within their AWS accounts, along with the associated APIs and services. IAM enables the management of user profiles and security credentials, including API access keys, to facilitate user access to AWS resources. This project will guide you through the fundamental aspects of IAM. Specifically, we will delve into user and group administration and demonstrate how to grant access to specific resources by utilizing IAM-managed policies. Additionally, we will explore how to locate the login URL, the portal through which AWS users can access their accounts, all while considering practical, real-world use cases.

Duplicate the IAM user sign-in link from the AWS console, launch an incognito window, and log in as user-1, user-2, and user-3 using the passwords provided on the lab page.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Sign in to the AWS Management Console:
- Access the IAM Dashboard:
- Create the Groups (if not already created)
- Add Users to Groups

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Sign in to the AWS Management Console:
    Log in to your AWS account using your credentials.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 Access the IAM Dashboard:
