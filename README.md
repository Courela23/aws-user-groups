# Creating Sysmon rules to detect Encoded PowerShell Malicious Scripts and Monitor RunOnce Registry Key Modifications

<h2> What is Sysmon ? </h2> Sysmon (System Monitor) is a Windows system service that logs detailed system activity, such as process creation and network connections. Organizations use Sysmon to detect and investigate security incidents by configuring rules to specify which events to log. These logs are then analyzed with SIEM tools to identify and respond to suspicious activities. Sysmon is installed on individual Windows endpoints, such as desktops, laptops, and servers, as part of an organization's security measures, either during the setup of new endpoints or when enhancing existing security infrastructure.
<h2> Overview</h2>

  1. Install Sysmon.
  2. Run an Encoded PowerShell Scripts (Check the Wazuh-SIEM to see if an alert was generated).
  3. Modify RunOnce Registry Key (Check the Wazuh-SIEM to see if an alert was generated).

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
- Using this prompt, to restart Wazuh.
    - Restart-Service -Name wazuh

<h2> Sysmon Rule # 1 (Encoded PowerShell Scripts)</h2>

![Screen Shot 2024-07-21 at 7 40 47 PM](https://github.com/user-attachments/assets/39601e50-bfae-4e7d-97ee-a4d3404046a0)


<h2> Why do attackers use Encoded scripts? </h2> Attackers use encoded scripts to evade detection by disguising the true intent of their commands to bypass signature-based systems. Leveraging PowerShell's capability to run Base64 encoded commands, they can execute malicious code stealthily without raising alerts. 

In this lab, we will be using Base64 to encode the get process command. The get process command shows all the programs/ processes running on your machine. 
 <h2>STEPS </h2> 
  
  1. Add a New Rules File in Wazuh GUI:
     - Navigate to Wazuh GUI and select Management -> Rules -> Manage Rule Files -> Add New Rules File.
  2. Create this Sysmon rule in Wazuh.
![Screen Shot 2024-07-18 at 8 10 11 PM](https://github.com/user-attachments/assets/1917792f-7ffc-46ad-9099-f8ca6e222649)
  3. Trigger the Rule using PowerShell:
     - Open Powershell as an admin and encode the "Get-Process". Remember that the ($) is used to assign variables. 
       - $command = 'Get-Process'
       - $bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
       - $encodedCommand = [Convert]::ToBase64String($bytes)
       - $encodedCommand
      - The output should look like this:
        - RwBlAHQALQBQAHIAbwBjAGUAcwBzAA==
      - Now we will run the encoded get process and see if the Wazuh-SIEM triggered an alert.
         - powershell.exe -EncodedCommand RwBlAHQALQBQAHIAbwBjAGUAcwBzAA==

![Screen Shot 2024-07-19 at 9 58 28 PM](https://github.com/user-attachments/assets/0dd1393d-5d0c-463d-81d8-bc8ec6585fe7)

<h2> Sysmon Rule # 2 (Windows Registry RunOnce Key Modification)</h2>

![Screen Shot 2024-07-21 at 8 46 49 PM](https://github.com/user-attachments/assets/2a318bee-e6ad-4d7a-913d-2b5d5c1424dd)
<h2> What is the Windows Registry? </h2> The Windows Registry is a hierarchical database that stores configuration settings and options for the Windows operating system and installed applications. It contains information, settings, and options related to hardware, software, users, and the system.

![Screen Shot 2024-07-19 at 10 00 59 PM](https://github.com/user-attachments/assets/d1de90a7-8cfb-4a80-bbab-53356b1d1c43)
<h2> How would an attacker utilize it? </h2>
Attackers can add entries to the registry to ensure their malicious code runs automatically each time the system starts or a user logs in. Common keys used for persistence include Run, RunOnce, and Startup.

 In this lab, we will be editing the Run/RunOnce key to run the calculator app every time the computer boots up. 
 <h2>STEPS</h2> 
   1. First we create the sysmon rule. 
   
![Screen Shot 2024-07-21 at 9 02 17 PM](https://github.com/user-attachments/assets/aab6b213-ec0d-493a-ae64-ac2247f06b17)
   
   
   2. Now we can edit the Windows Registry (Run it as an Admin) to open the calculator app upon bootup.
        - Navigate to the Run Key:
          - HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run.
          - Right-click on run\New\string Value\
          - Name it "Claculator"
          - Right-click on the name and select modify.
          - For value data type "calc.exe" and click "ok"

![Screen Shot 2024-07-21 at 9 38 07 PM](https://github.com/user-attachments/assets/1e253a52-af9c-4796-94e8-2ed58983f67a)


  3. Close the Registry Editor. The changes will take effect the next time you restart your computer.
![Screen Shot 2024-07-20 at 12 36 06 PM](https://github.com/user-attachments/assets/58c56c09-cc33-47f0-9414-27b9dc7674dc)
  
  4. Check the Wazuh SIEM to see the triggered alert. 
![Screen Shot 2024-07-20 at 12 19 48 PM](https://github.com/user-attachments/assets/75f4cf50-6713-415a-ac75-e862be6faf37)
