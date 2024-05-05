# Snort-Intrusion-Detection-System-Lab

Task 1: Introduction
Welcome to the Snort Challenge Lab! In this lab, you will learn the basics of writing IDS rules using Snort, a popular open-source intrusion detection system. The lab consists of two tasks: Introduction and Writing IDS Rules (HTTP). Let's get started!

Task 2: Writing IDS Rules (HTTP)
Q1: Write rules to detect “all TCP port 80 traffic” packets in the given pcap file.

![Screenshot 2024-05-05 12 26 30 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/0f3d7dec-75f2-4247-887e-8eecd4a9742a)

To detect all TCP port 80 traffic, we'll create two rules in the local.rules file:

![Screenshot 2024-05-05 12 26 30 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/93767677-bffc-4b4f-994e-cc2198e97a22)

Rule 1: Inbound traffic to port 80
alert tcp any any -> any 80 (msg: "Found"; sid: 100001; rev: 1;)

Rule 2: Outbound traffic from port 80
alert tcp any 80 -> any any (msg: "Found"; sid: 100002; rev: 2;)

Q2: What is the number of detected packets?

![Screenshot 2024-05-05 2 54 34 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/bb7472a6-39c9-4e12-84b8-c3a1eb372330)

![Screenshot 2024-05-05 3 00 08 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/ea1f6258-c530-4879-a32d-9cb7ca92bff2)

After running Snort against the pcap file (mx-3.pcap), the number of detected packets is 382.

Q3: What is the destination address of packet 63?
The destination address of packet 63 is 145.254.160.237.

Q4: What is the ACK number of packet 64?
The ACK number of packet 64 is 0x38AFFFF3.

Q5: What is the SEQ packet number of packet 62?
The SEQ packet number of packet 62 is 0x38AFFFF3.

Q6: What is the TTL of packet 65?
The TTL of packet 65 is 128.

Q7: What is the source IP and port of packet 65?
The source IP and port of packet 65 are 145.254.160.237:3372.

Conclusion
Congratulations! You've completed the Snort Challenge Lab. You've learned how to write IDS rules and analyze network traffic using Snort. Keep practicing and exploring to enhance your skills further.

Feel free to reach out if you have any questions or need further assistance.

Repository Structure
README.md: Overview of the lab
local.rules: IDS rules file
pcap/: Directory containing pcap files
log/: Directory containing log files
answers.md: Answers to the questions in the lab
You can structure your GitHub repository accordingly and include screenshots or additional resources as needed. Happy learning!
