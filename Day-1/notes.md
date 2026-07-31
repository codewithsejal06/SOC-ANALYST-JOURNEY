Part 1: What is Cybersecurity?

Cybersecurity is the practice of protecting computers, networks, applications, and data from unauthorized access, attacks, damage, or theft.

Real-Life Example:
Imagine your house.
🚪 Door Lock = Password
🎥 CCTV = Security Monitoring
👮 Security Guard = SOC Analyst
🚨 Alarm = Security Alert
🔑 House Key = Authentication
🏠 House = Computer System

Just as a house needs protection from burglars, digital systems need protection from cyber attackers.

Why Cybersecurity is Important?
Today almost everything is online:
Online banking
UPI payments
Shopping
Email
Hospitals
Universities
Government services

If these systems are attacked:

Money can be stolen.
Personal data can leak.
Businesses can stop working.
Critical services can fail.

That's why cybersecurity is essential.

************************

Part 2: Goals of Cybersecurity (CIA Triad)

The CIA Triad is the foundation of cybersecurity.

1. Confidentiality : Only authorized people should access information.
Example : Only you should be able to read your email.
How it's achieved:
Passwords
Encryption
Multi-Factor Authentication (MFA)

2. Integrity : Data should not be altered without permission.
Example : Your exam marks should not change unless an authorized teacher updates them.
How it's achieved:
Hashing
Digital Signatures
Access Controls

3. Availability : Systems should be available when users need them.
Example : Your bank's website should work whenever you log in.
Threat Example : A DDoS attack makes the website unavailable.

📌 Remember
CIA = Confidentiality + Integrity + Availability

************************

Part 3: What is a SOC?

A SOC (Security Operations Center) is a team of cybersecurity professionals who continuously monitor an organization's systems for suspicious activity and respond to security incidents.

Think of a SOC as the control room for an organization's security.

What Does a SOC Do?
A SOC team:
Monitors logs and alerts
Detects suspicious activity
Investigates incidents
Responds to attacks
Documents findings
Improves security over time

************************

Part 4: Who is a SOC Analyst?

A SOC Analyst is the first line of defence against cyber attacks.

Daily Responsibilities :
Monitor alerts in a SIEM
Investigate suspicious IP addresses
Analyse login failures
Detect malware
Review firewall logs
Escalate serious incidents
Document findings

A Day in the Life of a SOC Analyst
Imagine it's 9:00 AM , an alert appears:

"Multiple failed login attempts from IP 203.0.113.10."
As a SOC Analyst, you might:

Check which user account is affected.
Identify the source IP.
Determine whether it's internal or external.
Look for similar activity.
Decide whether it's a brute-force attack.
Escalate or close the alert.

************************

Part 5: SOC Team Structure

L1 Analyst
Monitors alerts
Performs initial investigation
Escalates complex cases

L2 Analyst
Performs deeper analysis
Contains incidents
Coordinates response

L3 Analyst
Threat hunting
Malware analysis
Detection engineering
Mentors junior analysts

************************

Part 6: Event vs Alert vs Incident

Event : Any activity on a system.
Examples :
User logs in
File is opened
Browser starts
Most events are normal.

Alert : A security tool detects something suspicious.
Example : 20 failed login attempts in one minute

An alert requires investigation.

Incident : An alert is confirmed to be a real security issue.
Examples :
Malware infection
Data breach
Ransomware attack

Not every alert becomes an incident.

************************

Part 7: SOC Workflow

Every investigation follows a process:

Event
   ↓
Alert
   ↓
Investigation
   ↓
Incident (if confirmed)
   ↓
Response
   ↓
Recovery
   ↓
Lessons Learned

************************

Part 8: Common SOC Tools

Tool	                                   Purpose

Splunk	                                   SIEM for collecting and searching logs
Microsoft Sentinel	                       Cloud SIEM and SOAR
Wazuh	                                   Open-source SIEM/XDR
Wireshark	                               Network packet analysis
Sysmon	                                   Detailed Windows event logging
VirusTotal	                               File and URL reputation checks
Nmap	                                   Network scanning
Zeek	                                   Network security monitoring