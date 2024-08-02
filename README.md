# Network Security Analysis Project

<h2> What is Wireshark? </h2> Wireshark is a powerful and widely used network protocol analyzer essential for network administrators, security professionals, and developers. It captures and displays network traffic in a detailed, human-readable format, supporting deep inspection of hundreds of protocols. Wireshark helps diagnose connectivity issues, identify security threats, and troubleshoot network problems by providing detailed packet information and robust filtering options. It runs on multiple operating systems and is backed by extensive documentation and community support. Whether for network troubleshooting, security analysis, or protocol development, Wireshark is an indispensable tool for gaining deep insights into network operations.
<h2> Overview</h2>


- In this project, I will analyze a . PCAP file containing network traffic from a host that made several suspicious requests to various domains on the internet.
   - https://www.malware-traffic-analysis.net/2021/01/05/index.html (Go to this link and download the 2021-01-05-PurpleFox-EK-and-post-infection-traffic.pcap.zip)

![image](https://github.com/user-attachments/assets/3c1eb358-4652-46ec-9a2f-7360e3928ab1)
   
   - The file is password protected, Therefore use the password credentials provided on the website to unzip the file. Then Open it with Wireshark.

- Step 1: Open the.PCAP file open answer the following questions.
    - Question 1: What is the total elapsed time of this PCAP (Hint: Statistics → File Properties)
      - The time elapsed for this PCAP was 00:21:23.

![image](https://github.com/user-attachments/assets/d822e776-4f35-4389-b8b1-5845db167209)
    
- Question 2: What is the Total number of Packets (Hint: Statistics → File Properties)
      - The total number of packets captured was 10, 389. 
    - Question 3: What destination IP addresses have the largest Bytes, list the top 5 (Hint: Statistics → Conversations → IPv4)
      - The top 5 IP addresses with the largest Bytes were.
        - 185.178.208.171 (5MB)
        - 60.12.109.73 (2MB)
        - 58.64.128.29 (1MB)
        - 172.64.166.10 (1MB)
        - 59.45.79.40 (108kB)
 
  ![image](https://github.com/user-attachments/assets/60db91c5-46ad-4da2-ab6d-c8998ff839de)


- Step 2: Search for GET Requests made, and answer the following questions.
   - Question 1: What is the total number of GET Requests made?
      - There were 10 get requests made.
   - Question 2: What is the Source IP that made these GET requests?
      - The source IP address for the Get Requests was: 10.1.5.101
 - Step 3: Right-click on the first GET request and select Follow Stream → HTTP
   - Question 1: What is the GET request that was made?
      - The GET request made was    /up.hph?key+ HTTP/1.1

![image](https://github.com/user-attachments/assets/a32b8d09-6ca0-4e09-a0bf-5dfd2ef5f046)
  
   - Question 2: What is the name of the website?
      - The name of the website is .githack.cyou
   - Question 3: Use OSINT to get the threat reputation of the domain, whats the score? 
      - According to OSSINT, the domain is malicious, its been flagged by several vendors as well.

![image](https://github.com/user-attachments/assets/1e274b9b-1513-4225-adae-9560d2122b3a)
   
   - Question 4: The Server responded to the GET request with a 200 OK what does this mean?
      - The server responded to the GET request with a 200 OK, which means the request was successful / Accepted.
  
