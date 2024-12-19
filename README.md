Network and Log Forensics: Identifying a Rogue User

## Objective

The purpose of this project is to simulate a real-world cybersecurity investigation within a Security Operations Center (SOC). The objective is to analyze network activity and logs to identify a rogue user within the company, "Boring Office," suspected of impersonating an employee and disseminating sensitive information. This project showcases the critical thinking, technical skills, and forensic methodologies used to resolve cybersecurity incidents and reinforces the importance of log analysis and network traffic investigation in modern cybersecurity operations.

### Project Goal
By completing this project, I aimed to achieve the following:

- Analyze Network Traffic:
   - Investigate a provided .pcap file to extract key network activity details, including identifying a specific user's IP address.
- Leverage DHCP Logs:
   - Use DHCP logs to correlate the identified IP address to a specific host device within the network.
- Investigate Security Logs:
    - Review account security logs to determine which user account was actively logged in to the identified host device, uncovering the rogue user's identity.

### Skills Used
This project was designed to strengthen several critical cybersecurity skills, including:

- Packet Analysis Skills:
  - Gain proficiency in using tools like Wireshark to analyze .pcap files and extract meaningful information, such as IP addresses and suspicious activity patterns.
- Log Correlation Techniques:
  - Develop the ability to cross-reference DHCP logs with network traffic to map an IP address to a specific physical or virtual host within an environment.
- User Attribution through Security Logs:
  - Understand how to analyze account security logs to identify user actions and attribute activity to a specific individual.
- Incident Investigation Workflow:
  - Experience the structured approach of a Blue Team investigation, including evidence collection, analysis, and identification of the responsible user.

## Step 1:  Find the IP Address

![wireshark 1](https://github.com/user-attachments/assets/e9ea9585-8b24-404a-8023-e8d576d2aceb)

1. Initial Packet Count:
 - After opening the .pcap file, observe the total packet count (e.g., 60 packets). This represents all captured network traffic.
2. Applying the First Filter:
 - Input the filter smtp in the "Apply a display filter..." field and press Enter.
 - This filter narrows down the results to packets using the Simple Mail Transfer Protocol (SMTP), which is used for email communication.
   ![smtp 1 ](https://github.com/user-attachments/assets/6f2cec54-ec7f-43de-b88c-9d045428ccf8)

3. Interpreting the Results:
 - The displayed packets will now only include SMTP traffic. This step is crucial for focusing the analysis on email-related activities within the network.
4. Refining the Filter Further:
 - To specifically locate packets containing a "FROM" field, which indicates the sender’s email address, refine the filter by inputting: (smtp contains "FROM")
 - This further reduces the displayed packets to those containing the keyword "FROM" within the SMTP protocol, allowing you to hone in on messages that may be tied to the rogue user.
![smtp_from](https://github.com/user-attachments/assets/9020a470-98b0-4617-8521-2844bff744a6)
 5. Analyze the Single Packet:
 - Observe that a single packet remains in the filtered results.
 - Check the info column to confirm that the packet is associated with the compromised user’s email account.
6. Identify the Source IP Address:
 - Locate the source IP address in the packet details: 10.10.1.4
 - This IP address indicates the network location of the rogue user’s activity.

Example below.

*Ref 1: Network Diagram*# Network-and-Log-Forensics-Identifying-a-Rogue-User
