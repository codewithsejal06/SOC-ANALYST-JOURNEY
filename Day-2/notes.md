# 1. What is a Network?

A computer network is a group of connected devices that communicate and share resources.

For example:

Laptop ─────┐
Phone  ─────┼──→ Router ──→ Internet
TV     ─────┘

Devices can communicate using agreed rules called protocols.

## Examples:

HTTP/HTTPS → Web communication
DNS → Domain-name resolution
SSH → Secure remote access
TCP/UDP → Transport communication
Why does this matter in SOC?

 Suppose your SIEM shows:

192.168.1.15 → 10.10.20.5:22

## You need to understand:

192.168.1.15 → source IP
10.10.20.5 → destination IP
22 → destination port
SSH → likely service

Without networking knowledge, the alert doesn't mean much.

---

# 2. LAN, WAN and Internet
LAN — Local Area Network

A network covering a small area.

Example:

Your Home
 ├── Laptop
 ├── Phone
 ├── Smart TV
 └── Router
WAN — Wide Area Network

Connects networks over large geographical areas.

The Internet is the largest example of an interconnected network.

---

# 3. Client and Server

A client requests a service.

A server provides that service.

## Example:

Your Browser
     │
     │ Request
     ↓
Web Server
     │
     │ Response
     ↓
Your Browser

When you open a website, your browser acts as a client and communicates with a web server.

---

# 4. IP Address

An IP address identifies a network interface so devices can communicate using IP.

An IPv4 address looks like:

192.168.1.10

It contains four numbers separated by dots.

Each part ranges from:

0 – 255
# Public vs Private IP
## Private IP 
Used within private networks.

Common private ranges include:

10.0.0.0 – 10.255.255.255

172.16.0.0 – 172.31.255.255

192.168.0.0 – 192.168.255.255

Example:

192.168.1.10

Your laptop might have a private IP assigned by your router.

## Public IP

Used to identify your network on the public Internet.

Your router typically communicates with the Internet using a public IP assigned by your ISP.

## SOC relevance

If a log shows:

Source IP: 192.168.1.20

that's a private address.

If it shows:

Source IP: <public address>

it may represent a system communicating across the Internet.

Important: An IP address alone does not automatically prove that an activity is malicious.