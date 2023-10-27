# aws-user-groups
<h1>Identity and Access Management (IAM) Deployed in the Cloud (AWS)

  ![Screen Shot 2023-10-25 at 4 38 51 PM](https://github.com/Courela23/aws-user-groups/assets/136120929/72bdc180-e2eb-4cb1-b260-64eb7779d305) </h1>



<h2>Environments and Technologies Used</h2>
  -A Cloud Guru.
<h1>Project Overview</h1>
The project involves AWS Identity and Access Management (IAM), a service designed for AWS customers to effectively oversee user access and permissions within their AWS accounts, along with the associated APIs and services. IAM enables the management of user profiles and security credentials, including API access keys, to facilitate user access to AWS resources. This project will guide you through the fundamental aspects of IAM. Specifically, we will delve into user and group administration and demonstrate how to grant access to specific resources by utilizing IAM-managed policies. Additionally, we will explore how to locate the login URL, the portal through which AWS users can access their accounts, all while considering practical, real-world use cases.

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
    Navigate to the IAM dashboard by clicking on "Services" in the top left corner, then selecting "IAM" under the Security, Identity, & Compliance section.

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the Groups (if not already created)
    If you haven't already created the necessary groups (S3-Support, EC2-Support, and EC2-Admin), you should create them first. To create a group:
        In the IAM dashboard, select "Groups" from the left-hand menu.
        Click the "Create group" button.
        Give the group a name (e.g., S3-Support), and then proceed to create the group.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Add Users to Groups:
    After the groups have been created, you can add users to them. Here's how:
        In the IAM dashboard, select "Groups" from the left-hand menu.
        Click on the name of the group (e.g., S3-Support) to which you want to add users.
        In the group details page, click the "Add users to group" button.
        Select the users you want to add (e.g., user-1), and then click the "Add users" button.

Repeat these steps for the other two groups (EC2-Support and EC2-Admin) and assign the respective users (user-2 and user-3) to their appropriate groups.

Once you've completed these steps, the specified users will be added to their respective groups in Amazon IAM, and they will inherit the permissions and policies associated with those groups.
