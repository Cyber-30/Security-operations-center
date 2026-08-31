# IP Addressing

An **IP (Internet Protocol) address** is a unique number assigned to every device on a network. It identifies the device and shows its location so data can be sent to the correct destination.

- **Purpose:** Identifies and locates devices on a network.
- **Example:** `192.168.1.10`
- **IPv4:** Uses **32 bits**, divided into **4 octets** (8 bits each).
- **Each octet:** Ranges from **0 to 255**.
- **Binary:** Computers store IP addresses in binary.
    - Example:
        - `192 = 11000000`
        - `168 = 10101000`
- **Why learn binary?** While SOC analysts rarely use binary every day, it is important for understanding **subnetting** and network troubleshooting.



# Network Part

The **Network Part** of an IP address identifies **which network** a device belongs to. It is like the **city or area** in a postal address.

**Example:**

- IP Address: `192.168.1.10`
- Network Part: `192.168.1` (assuming a `/24` subnet mask)

This means all devices with IP addresses like:

- `192.168.1.5`
- `192.168.1.20`
- `192.168.1.100`

belong to the **same network** and can communicate directly without a router. The last part (`.10`) identifies the specific device on that network.

# Host Part

The **Host Part** of an IP address identifies the **specific device** within a network. It is like the **house number** in a city address.

**Example:**

- IP Address: `192.168.1.10`
- Host Part: `10` (assuming a `/24` subnet mask)

This means:

- `10` is the unique device number on the `192.168.1` network.
- Every device in the same network must have a **different host number** to avoid IP address conflicts.

# Subnetting Basic

#### What is Subnetting?

**Subnetting** is the process of dividing a large network into **smaller subnetworks (subnets)**.

**Why use subnetting?**

- **Better security** – Separates different departments or systems.
- **Better performance** – Reduces network traffic and congestion.
- **Easier management** – Makes networks simpler to organize and troubleshoot.

---

### CIDR Notation

**Example:** `192.168.1.0/24`

- **`/24`** means:
    - **24 bits** are used for the **network part**.
    - **8 bits** are used for the **host part**.

This creates one network (`192.168.1.0`) with up to **254 usable host IP addresses** (from `192.168.1.1` to `192.168.1.254`).


# What is CIDR?

**CIDR (Classless Inter-Domain Routing)** is a method of assigning IP addresses and creating subnets more **flexibly** than the old class-based system.

**Why is CIDR used?**

- Efficient use of IP addresses (less waste)
- Flexible subnet creation
- Better network management and routing

# What is a /24 Subnet?

A **`/24`** means:

- **24 bits** are used for the **network part**.
- **8 bits** are used for the **host part**.

**Example:**

- Network: `192.168.1.0/24`
- Usable host IPs: `192.168.1.1` to `192.168.1.254`
- Total IP addresses: **256**
- Usable host addresses: **254** (excluding the network and broadcast addresses)

In simple terms, a **`/24` subnet** divides the IP address so that the first three octets identify the network, and the last octet identifies individual devices on that network.

## How Many IP Addresses Are in a `/24` Subnet? (Short Explanation)

A **`/24` subnet** contains **256 total IP addresses**.

**Formula:**

- **Total IPs = 2^(32 − Subnet Prefix)**
- **2^(32 − 24) = 2⁸ = 256**

**Reserved IP Addresses:**

- **Network Address:** First IP (e.g., `192.168.0.0`) – Identifies the subnet.
- **Broadcast Address:** Last IP (e.g., `192.168.0.255`) – Used to send data to all devices in the subnet.

**Usable IP Addresses:**

- **256 − 2 = 254 usable IPs**
- Usable range: `192.168.0.1` to `192.168.0.254`

# Subnetting Basics

| CIDR | Subnet mask   | Hosts  |
| ---- | ------------- | ------ |
| /24  | 255.255.255.0 | 254    |
| /16  | 255.255.0.0   | 65.634 |
| /8   | 255.0.0.0     | 16M    |

# Versions of IP Addresses

#### **IPv4 (Internet Protocol Version 4)**

- **Address size:** 32-bit
- **Format:** Decimal (e.g., `192.168.1.1`)
- **Total addresses:** About **4.3 billion** (`2³²`)
- **IPSec:** Optional
- **Status:** Most widely used, but limited addresses have led to address exhaustion.

#### **IPv6 (Internet Protocol Version 6)**

- **Address size:** 128-bit
- **Format:** Hexadecimal (e.g., `2001:db8::1`)
- **Total addresses:** About **3.4 × 10³⁸** (`2¹²⁸`)
- **IPSec:** Built into the protocol suite (support is mandatory in the specification, though use is not always required in practice).
- **Purpose:** Created to overcome IPv4 address shortages and support the growing number of internet-connected devices.

### Key Difference

- **IPv4:** 32-bit, decimal format, limited addresses.
- **IPv6:** 128-bit, hexadecimal format, enormous address space, designed for the future Internet.

# Classes of IP Addresses

#### **Class A**

- **Range:** `1.0.0.0` – `126.255.255.255`
- **Network bits:** 8
- **Host bits:** 24
- **Use:** Large networks
- **Example:** Government organizations and large enterprises
- **Note:** `127.x.x.x` is reserved for **loopback** (localhost).

#### **Class B**

- **Range:** `128.0.0.0` – `191.255.255.255`
- **Network bits:** 16
- **Host bits:** 16
- **Use:** Medium-sized networks
- **Example:** Universities and large companies.

#### **Class C**

- **Range:** `192.0.0.0` – `223.255.255.255`
- **Network bits:** 24
- **Host bits:** 8
- **Use:** Small networks
- **Example:** Home networks and small businesses

#### **Class D**

- **Range:** `224.0.0.0` – `239.255.255.255`
- **Use:** Multicast communication (sending data to multiple devices at the same time)
- **Example:** Video streaming, online webinars, and live broadcasts

#### **Class E**

- **Range:** `240.0.0.0` – `255.255.255.255`
- **Use:** Experimental and research purposes
- **Public Use:** Not used for normal public networking or assigning IP addresses to devices.

**Summary:**

- **Class A:** Large networks, more hosts.
- **Class B:** Medium-sized networks, balanced number of networks and hosts.
- **Class C:** Designed for small networks with fewer hosts.
- **Class D:** Reserved for multicast traffic, not for assigning IP addresses to individual devices.

# Types of IP Addresses

#### 1. Public IP Address

- A **Public IP** is assigned by an Internet Service Provider (ISP).
- It is **unique on the Internet** and allows devices to communicate over the internet.
- **Example:** `8.8.8.8`

#### 2. Private IP Address

- A **Private IP** is used inside local networks (home, office, etc.).
- It **cannot be accessed directly from the Internet**.
- Common private IP ranges:
    - `10.0.0.0 – 10.255.255.255`
    - `172.16.0.0 – 172.31.255.255`
    - `192.168.0.0 – 192.168.255.255`

#### 3. Static IP Address

- A **Static IP** is a **fixed IP address** that does not change.
- It is commonly used for **servers, websites, and network devices**.
- **Advantage:** Reliable and always reachable.

#### 4. Dynamic IP Address

- A **Dynamic IP** is **automatically assigned** by a **DHCP server**.
- It can change over time.
- Most home users receive dynamic IP addresses from their ISP.

# SOC Perspective

| IP Type | Meaning             |
| ------- | ------------------- |
| Private | Internal Traffic    |
| Public  | External Connection |

Example - 
Source: 192.168.1.10
Destination: 45.77.123.66

Internal -> External Communication

# MAC Address

#### What is a MAC Address?

A **MAC (Media Access Control) address** is a **unique hardware identifier** assigned to a network interface (such as a Wi-Fi or Ethernet adapter).

**Example:** `00:1A:2B:3C:4D:5E`

### Structure

- **48-bit** address
- Written in **hexadecimal** (six pairs of hexadecimal digits)

### Parts of a MAC Address

- **First 24 bits (OUI):** Identifies the **manufacturer** of the device.
- **Last 24 bits (Device ID):** Uniquely identifies the specific network interface.

### Key Points

- **IP Address:** Identifies a device's **location** on a network and can change.
- **MAC Address:** Identifies the device's **hardware** and is usually permanent.

**Easy to remember:**

- **IP Address = Device's network address (can change).**
- **MAC Address = Device's hardware identity (usually fixed).**

# ARP (Address Resolution Protocol)

**ARP (Address Resolution Protocol)** is used to **map an IP address to a MAC address** on a local network.

**ARP maps:**

- **IP Address → MAC Address**

### Example

A device wants to send data to `192.168.1.1` but only knows its IP address.

It sends an **ARP Request**:

> **"Who has 192.168.1.1? Tell me your MAC address."**

The device with IP `192.168.1.1` replies with its **MAC address**.

### Why ARP is Important

- Enables devices on the same LAN to communicate.
- Converts an **IP address** into the **physical (MAC) address** needed to deliver data.

**Easy to remember:**

- **IP = Logical address**
- **MAC = Physical address**
- **ARP = Finds the MAC address from an IP address**

# MAC Address vs IP Address


# Real SOC Scenario – ARP Spoofing (Short Explanation)

**Scenario:**  
Multiple devices are showing the **same MAC address** on the network.

**Likely Cause:**

- **ARP Spoofing (ARP Poisoning)**
- **Man-in-the-Middle (MITM) Attack**

**What happens?**  
An attacker sends **fake ARP replies**, making multiple devices believe that the attacker's MAC address belongs to another device (such as the gateway). As a result, network traffic is redirected through the attacker.

**SOC Analyst Action:**

- Check the **ARP table** for duplicate or unexpected MAC addresses.
- Compare MAC addresses with known network devices.
- Monitor for suspicious ARP traffic using tools like **Wireshark**.
- Isolate the affected device and investigate further.

**Easy to remember:**

- **Same MAC on multiple IPs = Possible ARP Spoofing → Potential MITM attack.**
