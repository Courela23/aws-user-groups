# Creating Sysmon rules to detect Encoded PowerShell Malicious Scripts and Monitor RunOnce Registry Key Modifications

<h2> What is Sysmon ? </h2> Sysmon (System Monitor) is a Windows system service that logs detailed system activity, such as process creation and network connections. Organizations use Sysmon to detect and investigate security incidents by configuring rules to specify which events to log. These logs are then analyzed with SIEM tools to identify and respond to suspicious activities. Sysmon is installed on individual Windows endpoints, such as desktops, laptops, and servers, as part of an organization's security measures, either during the setup of new endpoints or when enhancing existing security infrastructure.
<h2> Basic Prerequisites</h2>
  
- Install Oracle VirtualBox Download and install VirtualBox from VirtualBox's official site.
- Download Linux ISO Download the ISO file of your preferred Linux distribution from its official website.
- Create a New Virtual Machine Open VirtualBox, click "New", and follow the wizard to name your VM, select Linux as the type, allocate memory (2 GB recommended), and create a virtual hard disk (20 GB or more).
- Configure the Virtual Machine Go to VM "Settings": Adjust system settings, attach the Linux ISO under "Storage", and configure the network settings.
- Install Linux and Complete Setup Start the VM, boot from the ISO, follow the installation steps for the Linux distribution, remove the ISO, and restart the VM.
- Optional: Install VirtualBox Guest Additions for enhanced performance.

  ![Screen Shot 2024-07-07 at 8 26 52 PM](https://github.com/user-attachments/assets/b8ba8ae1-e3c3-4c17-ac50-48798c26d190)

<h2>Installing Wazuh Manager (Linux Commands)</h2>

- To ensure all systems are up to date, open the Terminal on the Ubuntu and type this command.

  - sudo apt-get update
  - sudo apt-get upgrade -y

- Download and run the installation assiatance using this command

  - curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

- Once installations has been confirmed (in this case user name and password will be provided in the terminal output).
- You can access the wazuh web interface with:
![Screen Shot 2024-07-09 at 9 20 32 PM](https://github.com/user-attachments/assets/e2a648f6-950b-45f0-bb7e-a2bbca1cd664)
  - ![Screen Shot 2024-07-14 at 7 28 17 PM](https://github.com/user-attachments/assets/1be23982-ced4-4b7b-a5cc-a5b48ea9e0d8)
- Then log in with the username & password credentials provided in the terminal.
- When first accessing the Wazuh dashboard, the browser may display a warning about the certificate not being issued by a trusted authority. You can can either accept the certificate as an exception or configure the system to use a certificate from a trusted authority.
- Additionally, installing an agent will be covered in another project (The agen will be collecting security-related data and sends it to the Wazuh manager for analysis. It monitors the system for various types of activity, including log events, file changes, and configurations, and it helps in detecting intrusions, ensuring compliance, and identifying vulnerabilities.) 
![image](https://github.com/user-attachments/assets/59ab7d27-b46a-41c1-83c7-bd6c13ead236)
