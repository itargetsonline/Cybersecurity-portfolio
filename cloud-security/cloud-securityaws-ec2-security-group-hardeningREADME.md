# AWS EC2 Security Group Hardening Lab

## Platform
Amazon Web Services (AWS)

## Lab Overview
This hands-on lab focuses on deploying a basic EC2 instance and applying **network-level security hardening** using AWS Security Groups.  
The goal was to reduce unnecessary exposure by applying **least-privilege access** to inbound network traffic.

This lab reflects real-world cloud security decisions commonly encountered in **Cloud Support**, **SOC**, and **entry-level cloud security** roles.

---

## Environment Details
- **Service:** Amazon EC2
- **Instance Type:** t3.micro
- **Operating System:** Ubuntu Linux
- **Region:** us-east-1
- **Network Control:** AWS Security Groups

---

## Initial Configuration (Insecure State)
- EC2 instance launched with a public IPv4 address
- Security Group inbound rule:
  - **SSH (TCP 22)**
  - **Source:** 0.0.0.0/0 (open to the internet)

### Security Risk Identified
- Exposed SSH service increases risk of:
  - Brute-force attacks
  - Unauthorized access attempts
  - Internet-wide scanning and exploitation

---

## Security Hardening Actions Performed
- Modified Security Group inbound rules:
  - Restricted **SSH (TCP 22)** access
  - Allowed SSH **only from my trusted public IP**
- Removed unrestricted public access
- Verified changes applied successfully

---

## Final Secure Configuration
- SSH access limited to a single trusted IP (`/32`)
- Reduced external attack surface
- Applied least-privilege network access principles

---

## Key Security Concepts Demonstrated
- Cloud network security fundamentals
- Security Group rule evaluation
- Least privilege access
- Exposure reduction
- Understanding cloud misconfigurations

---

## SOC & Cloud Relevance
This lab demonstrates:
- Awareness of common cloud security risks
- Ability to identify insecure defaults
- Practical remediation of network exposure
- Security-focused decision making in cloud environments

Relevant to roles such as:
- Cloud Support / Cloud Operations
- Junior Cloud Security roles
- SOC Analyst with cloud exposure

---

## Evidence & Screenshots

### EC2 Instance Running
![EC2 Instance Running](01-ec2-running.png)

### Insecure SSH Configuration (Before Hardening)
![SSH Open to Internet](02-ssh-open-before.png)

### Secure SSH Configuration (After Hardening)
![SSH Restricted to Trusted IP](03-ssh-restricted-after.png)

### EC2 Instance Tagging
![EC2 Tags](04-tags.png)
