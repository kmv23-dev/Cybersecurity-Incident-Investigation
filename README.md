# Cybersecurity Incident Detection & Network Traffic Analysis

## Overview

This project documents my investigation of a simulated malware incident using packet capture data from the Malware-Traffic-Analysis.net "First to Last" traffic analysis exercise.

The goal of the investigation was to identify the compromised Windows system, determine the affected user, analyze suspicious network activity, and document the security risks and recommended response actions.

## Tools Used

- Wireshark
- TCP/IP and HTTP traffic analysis
- NBNS
- Kerberos
- SMB/SAMR

## Investigation

I began with FormBook command-and-control (C2) alerts and analyzed the associated network traffic in Wireshark.

Through packet analysis and protocol correlation, I identified:

- Compromised IP address
- MAC address
- Windows hostname
- User account and associated user
- Connections to alert-associated external IP addresses
- TCP connection establishment
- Suspicious HTTP GET and POST activity

I also examined HTTP request and response data and documented network indicators associated with the incident.

## Key Findings

The compromised Windows endpoint initiated TCP connections to external IP addresses associated with the FormBook alerts.

Analysis of the traffic revealed:

- Successful TCP three-way handshakes
- HTTP GET activity associated with a C2 alert
- An HTTP POST containing a 909-byte form-urlencoded request body
- Repeated encoded-looking HTTP parameters
- HTTP 301 and 404 server responses

The POST contents were not decoded, so the underlying data and whether sensitive information was transmitted could not be determined from the packet capture alone.

## Incident Response Recommendations

Based on the network evidence, recommended actions included:

- Isolate the affected endpoint
- Investigate the system for malware and persistence
- Review the affected user's authentication activity
- Block confirmed malicious or alert-associated indicators where appropriate
- Search other systems and logs for similar indicators
- Remove or reimage the affected system as appropriate
- Continue monitoring for recurring suspicious traffic

## Evidence

Screenshots from the investigation are included in the Evidence folder. A complete incident analysis is available in the accompanying incident report.

## Source

Network traffic used in this project was obtained from the Malware-Traffic-Analysis.net "First to Last" training exercise (2026-08-09).

This project was completed in a controlled training environment for cybersecurity education.
