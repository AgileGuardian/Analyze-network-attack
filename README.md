# Analyze-network-attack

# PROJECTNAME

## Objective
**The objective is to Review the following scenario. Then complete an incident report.**

You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor. 

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.


The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen my understanding of network security, attack patterns, and defensive strategies.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Advanced Identification of different types of network attacks.
- Proficiency in Analyzing attack patterns and techniques.
- Ability to Understand the characteristics and impact of network attacks.
- Enhanced knowledge of network security and countermeasures.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used
[Bullet Points - Remove this afterwards]

- Network analysis tools (tcpdump, Wireshark) for capturing and examining network traffic.
- Net generation tools to create realistic network traffic and attack scenarios.

## Steps
![Screen Shot 2024-08-30 at 2 06 57 PM](https://github.com/user-attachments/assets/92fa7003-098c-4380-83d1-a67f9e386914)
<p>As you scroll through the rest of the log, you will notice the web server stops responding to  legitimate employee visitor traffic. The visitors receive more error messages indicating that they cannot establish or maintain a connection to the web server. a clear indication of an DoS via SYN flood attack.</p>  

![Screen Shot 2024-08-30 at 2 15 25 PM](https://github.com/user-attachments/assets/ab6896a8-1650-4e83-bf4c-2698d691f241)

Every screenshot should have some text explaining what the screenshot is about.
|     Explanation                                                        |                  Log entry                                                     |
|------------------------------------------------------------------------------------------------------------------------|------------|
|<p>When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. Explain the three steps of the handshake</p>
<p> 1. Step one the client ( computer, mobile phone, tablet, or else) sends a SYN request to a server in this case a DNS server.</p><p>2.  The Server is supposed to initiate a 3-factor handshake by sending a SYN ACKpacket which is permission to connect with the client.</p><p>3. Once the client receives permission to connect the SYN ACK message. The client accepts by sending an ACK message.  to start requesting a webpage from the server. This concludes the 3-factor handshake.</p><p>**Explanation of what happens when a malicious actor sends a large number of SYN packets all at once:** When a malicious actor sends an abnormal amount of SYN packets to the server the port of the server gets clogged by all of these packets at the same time and just simply crashes completely. And now it is rendered unusable for all other clients to this DNS server.</p><p>**Explanation of what the logs indicate and how that affects the server**: The log indicates that the attack started at 3.390692 seconds of the log registry. The red is the attacker and it started sending SYN requests at a slow rate that was manageable for the server. In green we can see that it was able to answer normal clients at this point employees were still able to do a  SYN/ACK and request the web server they needed.</p><p>In the last 20 rows, we can see that the server is increasingly struggling to serve its clients. The attacker sends several SYN requests every second. In yellow we can see that legitimate employee communication requests started to fail all communication with the webserver(gateway timeout). All other communication fails at 20.167744 seconds the server is overloaded and cashed unable to respond to any clients. They can only receive error messages indicating that they cannot connect to the web server’s services.</p><p>The main characteristic of this type of attack is that one actor is sending only SYNK messages to the server. The effect is that none of the workforce can access the websites to continue their valuable work in the office network. Which costs a lot of money to the company that can’t continue their business. This attack could lead to desperate employees trying to use an unsecure network to access the website which could leave an open door for the attacker to get inside of the system. To prevent this attack we would suggest having a firewall that blocks any multi SYN request from one IP address or blocks all outsider IP address masquerading as one that is inside the network.</p>| Notice that the handshake process takes a few milliseconds to complete. Then, you can identify the employee’s browser requesting the sales.html webpage using the HTTP protocol at the application level of the TCP/IP model. Followed by the web server responding to the request.![Screen Shot 2024-08-30 at 2 22 07 PM](https://github.com/user-attachments/assets/8d296ed1-cf5f-427b-a9b3-7aac4b703fbf)|
Example below.

*Ref 1: Network Diagram*
