# What is OSI Model?
The OSI Model (Open Systems Interconnection) is a 7-layer framework that explains how data travels from one system to another. Think of it as a step-by step journey of data.

![[Pasted image 20260717012244.png|697]]


| Layer No. | Layer Name   | Example            |
| --------- | ------------ | ------------------ |
| 7         | Application  | Http, Ftp          |
| 6         | Presentation | Encryption         |
| 5         | Session      | Session Management |
| 4         | Transport    | TCP/UDP            |
| 3         | Network      | IP                 |
| 2         | Data Link    | MAC                |
| 1         | Physical     | Cables             |

## Application Layer

The application layer is the topmost layer of the OSI model and is closest to the end user. This layer provides the interface for users and software applications to interact with the network. It handles high-level functions like file transfers, email, and web browsing.

### Examples

- **Web Browsing**
    - Allows users to access websites and web applications through a browser.
- **Email**
    - Enables sending and receiving electronic messages over a network.
- **File Transfer**
    - Allows users or systems to upload, download, and share files between devices.

### Protocols

- **HTTP (Hypertext Transfer Protocol)**
    - Transfers web pages and data between a web browser and a web server. Data is not encrypted.
- **HTTPS (Hypertext Transfer Protocol Secure)**
    - A secure version of HTTP that encrypts communication using TLS/SSL to protect sensitive data.
- **FTP (File Transfer Protocol)**
    - Used to transfer files between computers over a network. Standard FTP does not encrypt data.
- **SMTP (Simple Mail Transfer Protocol)**
    - Used to send emails from a client to a mail server or between mail servers.
## SOC Perspective

### Phishing Attacks

- **What it is:** Fake emails or websites designed to steal credentials or install malware.
- **Why SOC monitors it:** To prevent users from giving away sensitive information, reduce malware infections, and stop account compromise before attackers gain access.

### Malicious URLs

- **What it is:** Links that lead to phishing pages, malware downloads, or command-and-control servers.
- **Why SOC monitors it:** Detecting and blocking malicious URLs helps prevent malware infections, credential theft, and unauthorized access to the organization's systems.

### Suspicious API Calls

- **What it is:** Unusual or unauthorized requests made to web applications or services through APIs.
- **Why SOC monitors it:** Attackers often abuse APIs to steal data, bypass authentication, or exploit application vulnerabilities. Monitoring API activity helps identify attacks such as data exfiltration, brute-force attempts, and abuse of application functionality.

## Presentation Layer

The presentation layer is responsible for the translation, encryption, and compression of data.

It ensures that data sent from the application layer is in a format that can be understood by the receiving system.

This layer often handles tasks like data formatting, character encoding (e.g., ASCII to Unicode), and data encryption.

### Functions

- **Data Formatting**
    - Converts data into a format that both the sender and receiver can understand (e.g., text, images, videos).
- **Encryption / Decryption**
    - Encrypts data before transmission to protect confidentiality and decrypts it when received.

### Examples

- **SSL/TLS (Secure Sockets Layer / Transport Layer Security)**
    - Encrypts communication between clients and servers, such as HTTPS websites, to keep data secure.
- **Encoding**
    - Converts data into a standard format (e.g., UTF-8, ASCII, Base64) so different systems can correctly interpret it.

## SOC Perspective

### Encryption Analysis

- **What it is:** Monitoring encrypted traffic and TLS certificates without necessarily decrypting the content.
- **Why SOC monitors it:** Attackers often hide malware communication inside encrypted traffic. SOC analysts look for suspicious certificates, unusual encrypted connections, expired/self-signed certificates, or abnormal traffic patterns to detect malicious activity.

### SSL Stripping (Man-in-the-Middle Attack)

- **What it is:** An attacker downgrades a secure HTTPS connection to an unencrypted HTTP connection, allowing them to intercept or modify data.
- **Why SOC monitors it:** SSL stripping can expose usernames, passwords, and sensitive information. Detecting it helps prevent credential theft, data interception, and unauthorized access to systems.

## Session Layer

The session layer establishes, manages, and terminates sessions between two communicating devices. It ensures that data exchange is synchronized and allows applications to communicate effectively without interference.
### Examples

- **Login Session**
    - Maintains a user's authenticated connection after they successfully log in, so they don't need to re-enter credentials for every request.
- **Session Cookies**
    - Small pieces of data stored by the browser that identify a user's active session and keep them logged in between requests.

---

## SOC Perspective

### Session Hijacking

- **What it is:** An attacker steals a user's active session ID or cookie to impersonate the user without knowing their password.
- **Why SOC monitors it:** It can allow attackers to access user accounts, steal sensitive data, or perform unauthorized actions. Detecting unusual session behavior helps prevent account compromise.

### Token Reuse

- **What it is:** A stolen or leaked authentication token (such as a JWT or API token) is reused by an attacker to access a system.
- **Why SOC monitors it:** Reused tokens from different devices, locations, or at unusual times may indicate a compromised account. Monitoring token usage helps detect unauthorized access and prevent data breaches.

## Transport Layer

The transport layer ensures the reliable delivery of data between two devices across a network. It segments the data received from the upper layers and provides error detection and correction. Additionally, it controls flow to prevent congestion and guarantees that data is delivered in the correct order.

### Functions

- **End-to-End Communication**
    - Enables reliable communication between applications running on different devices.
- **Reliability**
    - Ensures data is delivered accurately, retransmits lost packets, and maintains the correct order when using reliable protocols.

### Protocols

- **TCP (Transmission Control Protocol)**
    - A reliable, connection-oriented protocol that guarantees data delivery, correct order, and error checking.
- **UDP (User Datagram Protocol)**
    - A fast, connectionless protocol that sends data without guaranteeing delivery or order, making it suitable for real-time applications.

---

## SOC Perspective

### Port Scanning

- **What it is:** An attacker scans a system to identify open ports and the services running on them.
- **Why SOC monitors it:** Port scanning is often the first step in an attack. Detecting it early helps identify reconnaissance activity before attackers attempt exploitation.

### SYN Flood Attacks

- **What it is:** A type of Denial-of-Service (DoS) attack where an attacker sends a large number of TCP SYN requests without completing the connection.
- **Why SOC monitors it:** SYN floods can exhaust server resources and make services unavailable. Early detection helps reduce downtime and mitigate the attack.

### Suspicious Ports

- **What it is:** Unusual or unexpected network activity on specific port numbers.
- **Why SOC monitors it:** Attackers may use uncommon ports, unauthorized services, or backdoors to communicate with compromised systems. Monitoring ports helps detect malware, unauthorized services, and potential intrusions.

## Network Layer

The network layer is responsible for determining the best path to send data across multiple networks.

This layer handles logical addressing and routing, enabling data to travel from one network to another, regardless of the physical infrastructure.

Routers operate at this layer, forwarding data between different networks based on IP addresses.

### Functions

- **Routing**
    - Determines the best path for data packets to travel from the source to the destination across multiple networks.
- **IP Addressing**
    - Assigns and uses unique IP addresses to identify devices and ensure packets reach the correct destination.

### Protocol

- **IP (Internet Protocol - IPv4 / IPv6)**
    - The primary protocol used for addressing and routing packets across networks. IPv4 uses 32-bit addresses, while IPv6 uses 128-bit addresses to support a much larger address space.

---

## SOC Perspective

### IP Tracking

- **What it is:** Monitoring the source and destination IP addresses involved in network communication.
- **Why SOC monitors it:** Tracking IPs helps identify attackers, compromised devices, suspicious communication, and the origin of malicious traffic.

### Geolocation

- **What it is:** Mapping an IP address to its approximate geographic location.
- **Why SOC monitors it:** Connections from unexpected countries or regions may indicate unauthorized access, compromised accounts, or attacker activity.

### Suspicious External Connections

- **What it is:** Connections between internal systems and unknown or untrusted external IP addresses.
- **Why SOC monitors it:** Such connections may indicate malware communicating with command-and-control (C2) servers, data exfiltration, or unauthorized remote access, allowing analysts to detect and respond to threats quickly.

## Data Link Layer

The data link layer sits above the physical layer and is responsible for the reliable transfer of data across a physical network link.

This layer ensures that data is error-free and properly framed for transmission.

It also manages how devices on the same local network communicate with each other.

### Functions

- **MAC Address Communication**
    - Uses unique MAC (Media Access Control) addresses to identify devices and deliver data within the local network.
- **Local Network Delivery**
    - Transfers data frames between devices connected to the same LAN, such as computers connected to the same switch.

---

## SOC Perspective

### ARP Spoofing (Man-in-the-Middle Attack)

- **What it is:** An attacker sends fake ARP messages to associate their MAC address with another device's IP address, such as the default gateway.
- **Why SOC monitors it:** ARP spoofing allows attackers to intercept, modify, or steal network traffic. Detecting it helps prevent Man-in-the-Middle (MITM) attacks and unauthorized access.

### MAC Anomalies

- **What it is:** Unusual or unexpected MAC address activity, such as duplicate MAC addresses, frequent MAC address changes, or unknown devices appearing on the network.
- **Why SOC monitors it:** MAC anomalies may indicate device spoofing, rogue devices, or unauthorized network access. Monitoring them helps identify potential security incidents and insider threats.

## Physical Layer

The physical layer is the lowest layer of the OSI model, and it deals with the actual transmission of raw binary data (1s and 0s) over a physical medium, such as cables, fiber optics, or wireless signals.

It defines the hardware elements involved in data transfer, such as network interfaces, cables, switches, and the electrical signals used to carry the data.

### What it does

The **Physical Layer** is the lowest layer of the OSI model. It is responsible for transmitting raw bits over the physical medium using electrical, optical, or wireless signals.

### Functions

- **Hardware Transmission**
    - Transmits data through physical devices such as cables, network interface cards (NICs), switches, fiber optics, or wireless hardware.
- **Electrical Signals**
    - Converts digital data into electrical, optical, or radio signals for transmission and converts received signals back into data.

---

## SOC Perspective

### Rarely Used Directly

- **What it is:** The Physical Layer is not commonly monitored by SOC analysts because it does not contain application or network traffic details.
- **Why SOC monitors it:** While daily SOC operations focus on higher layers, physical issues can still affect security. Analysts may investigate physical tampering, cable disconnections, or device failures during incident response.

### Hardware Attacks

- **What it is:** Attacks that involve physical access to networking devices or infrastructure, such as unplugging cables, installing rogue devices, or tampering with hardware.
- **Why SOC monitors it:** Hardware attacks can bypass software security controls, enable unauthorized network access, or disrupt services. Monitoring physical security events helps detect sabotage, rogue devices, and unauthorized access to critical infrastructure.

# How does communication happen in the OSI Model ?

Communication in the OSI Model follows a systematic process called Encapsulation and Decapsulation:

1. Sender’s Side:

	● Data is generated at the application layer and moves downward through the layers.
	● Each layer adds its own header, and sometimes a footer, encapsulating the data with layer-specific information (e.g., addressing, error checks).

2. Transmission:

	● The encapsulated data (now called a packet) is transmitted over the physical medium to the receiving device.

3. Receiver’s Side:

	● The process is reversed as data moves upward through the OSI layers.
	● Each layer removes its corresponding header/footer (decapsulation) until the original data is presented to the receiving application.

Note : This structured approach ensures data integrity and reliability, even over complex networks.

![[Pasted image 20260717014723.png|697]]


# What is TCP/IP Model (Real-World Model) ?

The **TCP/IP model** (Transmission Control Protocol/Internet Protocol) is a four-layered networking framework that standardizes data communication, serving as the foundational architecture for the internet.

![[Pasted image 20260717014915.png|697]]


| TCP/IP Layer   | Maps TO OSI |
| -------------- | ----------- |
| Application    | OSI 7,6,5   |
| Transport      | OSI 4       |
| Internet       | OSI 3       |
| Network Access | OSI 2,1     |
# OSI vs TCP/IP (Important For Interviews)

| Features   | OSI        | TCP/IP    |
| ---------- | ---------- | --------- |
| Layers     | 7          | 4         |
| Use        | Conceptual | Practical |
| Real Usage | Less       | High      |
# SOC Example Mapping

Alert : Suspicious login via HTTPS from unknown IP

Analysis:
- Application Layer = HTTP Login
- Transport = Port 443
- Network = External IP
- Data link layer = Internal Network

# SOC Analyst Thinking

Whenever you see a log, break it like:

Which layer is involved?

Example:
- Port Usage -> Transport
- IP Issue -> Network
- DNS Issue -> Application
- ARP Issue -> Data Link

