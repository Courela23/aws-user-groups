# Creating Sysmon rules to detect Encoded PowerShell Malicious Scripts and Monitor RunOnce Registry Key Modifications

<h2> What is Sysmon ? </h2> Sysmon (System Monitor) is a Windows system service that logs detailed system activity, such as process creation and network connections. Organizations use Sysmon to detect and investigate security incidents by configuring rules to specify which events to log. These logs are then analyzed with SIEM tools to identify and respond to suspicious activities. Sysmon is installed on individual Windows endpoints, such as desktops, laptops, and servers, as part of an organization's security measures, either during the setup of new endpoints or when enhancing existing security infrastructure.
<h2> Basic Prerequisites</h2>
  
- Install Wazuh SIEM/ADD an Agent to collect logs

<h2> Installing Sysmon (windows 10)</h2>

- Download Sysmon (https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
- Open Powershell and enter the following prompt.
   - sysmon.exe -accepteula -i sysmonconfig.xml
- Configure Wazuh to capture Sysmon Events.
   - Open PowerShell as Administrator and navigate to the ossec-agent directory using this command:
     - cd "C:\Program Files (x86)\ossec-agent"
   - Open ossec.conf file using:
     - notepad.exe ossec.conf
- Add the necessary (Highlighted in BLUE) settings to the configuration file (notepad) to capture Sysmon event.
![Screen Shot 2024-07-21 at 7 05 55 PM](https://github.com/user-attachments/assets/988959ed-56c9-49b1-abb9-b3c73a358531)
- Using this prompt, restart wazuh
    - Restart-Service -Name wazuh


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
