# Snort-Intrusion-Detection-System-Lab

<h2> TASK #1: Writing IDS Rules (HTTP)</h2>

Welcome to the Snort Challenge Lab! In this lab, the basics of writing IDS rules will use Snort, a popular open-source intrusion detection system. The lab consists of Writing IDS Rules (HTTP).

Q1: Write rules to detect “all TCP port 80 traffic” packets in the given pcap file.

![Screenshot 2024-05-05 12 26 30 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/0f3d7dec-75f2-4247-887e-8eecd4a9742a)

To detect all TCP port 80 traffic, we'll create two rules in the local.rules file:

Rule 1: Inbound traffic to port 80
alert tcp any any -> any 80 (msg: "Found"; sid: 100001; rev: 1;)

Rule 2: Outbound traffic from port 80
alert tcp any 80 -> any any (msg: "Found"; sid: 100002; rev: 2;)

Q2: What is the number of detected packets?

![Screenshot 2024-05-05 2 54 34 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/bb7472a6-39c9-4e12-84b8-c3a1eb372330)

![Screenshot 2024-05-05 3 00 08 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/ea1f6258-c530-4879-a32d-9cb7ca92bff2)

After running Snort against the pcap file (mx-3.pcap), the number of detected packets is 382.

Q3: What is the destination address of packet 63?

![Screenshot 2024-05-05 3 13 28 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/49f87d14-1f55-41a8-a218-54689dc9eeae)

![Screenshot 2024-05-05 3 17 42 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/16dd197c-6ee6-478c-a14a-ba1f098b232e)

The destination address of packet 63 is 145.254.160.237.

Q4: What is the ACK number of packet 64?

![Screenshot 2024-05-05 3 29 30 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/73532487-d1c5-437b-9acc-479cca139e39)


![Screenshot 2024-05-05 3 29 30 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/31d123b8-9ae5-4f59-88da-ed4622def13c)

The ACK number of packet 64 is 0x38AFFFF3.

Q5: What is the SEQ packet number of packet 62?

![Screenshot 2024-05-05 3 32 24 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/af0cc08f-e39b-49c3-9ce9-b1b1bfc6fa53)

![Screenshot 2024-05-05 3 33 41 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/f66287f3-1709-4fde-ad6a-ffff06838cc4)

The SEQ packet number of packet 62 is 0x38AFFFF3.

Q6: What is the TTL of packet 65?
![Screenshot 2024-05-05 3 39 43 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/362b7eb9-dc76-4014-97b6-47d3648e8f78)

![Screenshot 2024-05-05 3 41 44 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/7ccad9eb-e5e8-4fce-a9be-9e202feac473)

The TTL of packet 65 is 128.

Q7: What is the source IP and port of packet 65?

The source IP and port of packet 65 are 145.254.160.237:3372.

<h2>Task 2: Writing IDS Rules (FTP) </h2>

In this task, we'll focus on writing IDS rules to detect FTP traffic. 

Q1: Write rules to detect “all TCP port 21” traffic in the given pcap.
Add the following rules to the local.rules file:
plaintext
Copy code
Rule 1: Inbound FTP traffic

alert TCP any 21 -> any any (msg: "FTP traffic Detected"; sid: 100001; rev: 1;)

Rule 2: Outbound FTP traffic

alert TCP any any -> any 21 (msg: "FTP traffic Detected"; sid: 100002; rev: 1;)

![Screenshot 2024-05-05 4 05 02 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/900cd267-dbc1-407b-8865-412e40550b77)

![Screenshot 2024-05-05 4 20 54 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/7d04e345-0789-480a-bd41-8e057bda8632)


![Screenshot 2024-05-05 4 19 32 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/bb9fe478-e914-4269-80db-2e01bab33e46)

After running Snort against the pcap file (ftp-png-gif.pcap), the number of detected packets is 614.

Q2: What is the FTP service name?

![Screenshot 2024-05-05 4 33 07 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/80120a86-ff93-4e1b-bc7a-6098ac6af9bb)

![Screenshot 2024-05-05 4 31 51 PM](https://github.com/mmedinabet/Snort-Intrusion-Detection-System-Lab/assets/142737434/cb2fd06f-bc8b-4f44-9afd-2d0892c52774)

The FTP service name is "Microsoft FTP service."

Q3: Write a rule to detect failed FTP login attempts in the given pcap.
Add the following rule to the local.rules file:

plaintext
Copy code

sudo snort -c local.rules -A full -l . -r ftp-png-gif.pcap


The number of detected packets for failed FTP login attempts is 41.

Q4: Write a rule to detect successful FTP logins in the given pcap.
Add the following rule to the local.rules file:

plaintext
Copy code
alert TCP any any <> any 21 (msg:"FTP Success Login"; content:"230 User"; sid:100004; rev:1;)
The number of detected packets for successful FTP logins is 1.

Q5: Write a rule to detect failed FTP login attempts with a valid username but a bad password or no password.
Add the following rule to the local.rules file:

plaintext
Copy code
alert tcp any any <> any 21 (msg: "FTP Failed Login-Bad or No Password"; content:"331 Password"; sid: 100005; rev: 1;)
The number of detected packets for failed FTP login attempts with bad or no password is 42.

Q6: Write a rule to detect failed FTP login attempts with the username "Administrator" but a bad password or no password.
Add the following rule to the local.rules file:

plaintext
Copy code
alert tcp any any <> any 21 (msg: "Failed Admin Login Attempt"; content:"Administrator"; content:"331 Password"; sid: 100006; rev: 1;)
The number of detected packets for failed FTP login attempts with the username "Administrator" is 7.
