# 1. What is a Network?

A computer network is a group of connected devices that communicate and share resources.

For example:

- Laptop ─────┐
- Phone  ─────┼──→ Router ──→ Internet
- TV     ─────┘

Devices can communicate using agreed rules called protocols.

## Examples:

- HTTP/HTTPS → Web communication
- DNS → Domain-name resolution
- SSH → Secure remote access
- TCP/UDP → Transport communication
- Why does this matter in SOC?

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
- Laptop
- Phone
- Smart TV
- Router


WAN — Wide Area Network

Connects networks over large geographical areas.

The Internet is the largest example of an interconnected network.

---

# 3. Client and Server

A client requests a service.

A server provides that service.

## Example:

**Your Browser**

↓ Request

**Web Server**

↓ Response

**Your Browser**

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

---

# 5. IPv4 vs IPv6

You'll encounter two major versions of IP.

## IPv4

Example:

192.168.1.10

IPv4 uses 32-bit addresses.

## IPv6

Example:

2001:db8::1

IPv6 uses 128-bit addresses.

IPv6 provides a vastly larger address space.

---

# 6. MAC Address

A MAC (Media Access Control) address is a link-layer identifier associated with a network interface.

Example:

00:1A:2B:3C:4D:5E

## IP vs MAC
Think of it like this:

- IP → network-level addressing

- MAC → local network/link-level addressing

Don't memorize the oversimplified idea that "IP is the address and MAC is the identity." In real networking, the details are more nuanced.

---

# 7. What is a Router?

A router connects different networks and forwards packets between them.

Example:

Your Laptop

↓

Home Router

↓

ISP Network

↓

Internet

↓

Web Server

Your home router commonly acts as the gateway between your local network and the Internet.

---

# 8. What is a Switch?

A network switch connects devices within a LAN.

Example:

PC ─────┐

Laptop ─┼──→   Switch

Server ─┘

A switch primarily operates using MAC addresses at the data-link layer.

A router primarily forwards traffic between different IP networks.

---

# 9. DNS — Domain Name System

This is extremely important for SOC analysts.

Humans prefer:

google.com

Computers communicate using IP addresses.

DNS helps resolve a domain name to an IP address.

## Conceptually:

You type:

example.com

↓

DNS Query

↓

DNS Response

↓

IP Address

## SOC Example

Suppose a workstation suddenly makes hundreds of DNS queries to strange domains.

A SOC analyst might investigate:

- Which machine generated them?
- Which user was logged in?
- What domains were requested?
- Are the domains suspicious?
- Did the machine make other unusual connections?

DNS logs can therefore be valuable evidence.

---

# 10. Ports

An IP identifies the destination host, while a port number helps identify the application/service endpoint.

Ports range from:

0 – 65535

## Some common ports:

| Port | Common Protocol/Service |
|---|---|
| 21 | FTP |
| 22 | SSH |
| 23	| Telnet |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 110 | POP3 |
| 143 | IMAP |
| 3389 | RDP |
| 443 |	HTTPS |

## Example
10.0.0.5:443

Means traffic is going to:

IP:   10.0.0.5
Port: 443

Port 443 is commonly associated with HTTPS.

---

# TCP vs UDP

This is another must-know SOC concept.

# 11. TCP

TCP is connection-oriented and provides mechanisms for reliable, ordered delivery.

It's commonly used when reliable communication matters.

Examples include:

- HTTPS
- SSH
- SMTP

## TCP 3-Way Handshake

## You may see:

|   Client   |    Server    |
|-------|-------|
| SYN  ────────────────→ |  |
|  | ←───────────── SYN-ACK |
| ACK  ────────────────→ | |


  Connection established

## Remember:

SYN → SYN-ACK → ACK

We'll analyse this in Wireshark later.

# 12. UDP

UDP is connectionless and has lower protocol overhead than TCP.

It doesn't provide TCP-style connection establishment or guaranteed delivery.

Common examples include:

- DNS
- DHCP
- Some streaming/real-time applications

For a SOC analyst, understanding TCP vs UDP helps you interpret network traffic.

---

# 13. HTTP vs HTTPS
## HTTP

Usually:

- Port 80

HTTP traffic isn't protected by TLS.

## HTTPS

Usually:

- Port 443

HTTPS uses TLS to provide encryption and authentication for the connection.

So:

HTTP  → generally unencrypted application traffic

HTTPS → HTTP protected by TLS

Important: Port 443 itself doesn't magically make traffic secure. HTTPS/TLS is what provides the security properties.

---

# 14. What Happens When You Open a Website?

Suppose you enter:

https://example.com

A simplified flow is:

1. Browser

   ↓

2. DNS resolution

   ↓

3. Server IP obtained

   ↓ 

4. Network connection established

    ↓

5. TLS negotiation for HTTPS
     
    ↓

6. HTTP request
     
    ↓

7. Web server responds
     
    ↓

8. Browser displays the page

A real browser may use caching, connection reuse, HTTP/2 or HTTP/3, and other mechanisms, but this simplified model is perfect for your current level.