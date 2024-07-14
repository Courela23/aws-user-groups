# Utilizing Linux Command Lines to Install a Wazuh - SIEM

<h2> What is Wazuh ? </h2> Wazuh is an open-source security monitoring platform that integrates multiple security functionalities to detect threats, monitor integrity, and ensure compliance with regulatory requirements. It offers intrusion detection, log data analysis, file integrity monitoring, vulnerability detection, and configuration assessment, helping organizations comply with standards like GDPR, HIPAA, and PCI DSS. Wazuh collects and processes security data from endpoints and network devices, generates real-time alerts based on customizable rules, and visualizes this information through its Kibana plugin.
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

  - sudo apt-get update && sudo apt-get upgrade -y
  - sudo apt-get install curl apt-transport-https lsb-release gnupg2 -y

- Download and run the installation assiatance using this command

  - curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

- Once installations has been confirmed (in this case user name and password will be provided in the terminal output).
- You can access the wazuh web interface with:
  - https://<wazuh-dashboard-ip>
- Then log in with the username & password credentials provided in the terminal.
  



Once you've completed these steps, the specified users will be added to their respective groups in Amazon IAM, and they will inherit the permissions and policies associated with those groups.
