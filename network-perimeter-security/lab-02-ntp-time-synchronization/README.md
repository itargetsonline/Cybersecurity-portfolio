# Lab 02 – NTP Time Synchronization (Cisco Packet Tracer)

Hands-on configuration and validation of a secure Network Time Protocol (NTP) hierarchy including authentication, synchronization testing, and time integrity validation across network devices.

---

## Objective

Design and configure a secure NTP infrastructure to ensure accurate log timestamps, secure authentication, and reliable time synchronization across routers within a controlled network environment.

Accurate time synchronization is critical for:

- SIEM log correlation  
- Incident response timelines  
- Forensic investigations  
- Network device coordination  
- Security monitoring accuracy  

---

## Lab Environment

- Cisco Packet Tracer 8.x  
- 2x Cisco 2901 Routers (R1, R2)  
- 1x Cisco 2960 Switch (S1)  
- 1x NTP Server  
- Private Subnet: 10.1.1.0/24  

---

## Network Topology

![Network Topology](01-topology-diagram.png)

---

## Initial IP Configuration (R1)

Verified IP addressing and interface configuration.

![R1 IP Configuration](02-r1-ip-configuration.png)

---

## NTP Server Configuration

Configured the NTP server with authentication key to prevent unauthorized synchronization.

![NTP Server Configuration](03-ntp-server-configuration.png)

---

## R1 as Authenticated NTP Client

R1 configured to synchronize with the NTP server using authentication.

Key configurations included:

```
ntp authentication-key 1 md5 <password>
ntp authenticate
ntp trusted-key 1
ntp server 10.1.1.100 key 1
```

![R1 NTP Client Configuration](04-r1-ntp-client-authentication.png)

---

## NTP Synchronization Verification

Synchronization status verified using:

```
show ntp status
show ntp associations
show clock
```

Confirmed that R1 successfully synchronized with the NTP server.

![R1 NTP Status](05-r1-ntp-status-synchronized.png)

---

## Clock Drift and Time Manipulation Test

After modifying the NTP server time, R1 detected time discrepancy and resynchronized automatically.

This demonstrates how NTP protects time integrity across devices.

![Clock Out of Sync](06-r1-clock-out-of-sync.png)

---

## R1 as Internal NTP Master

Configured R1 to act as an internal NTP master for downstream devices.

Command used:

```
ntp master
```

![R1 NTP Master Enabled](07-r1-ntp-master-enabled.png)

---

## R2 Synchronizing from R1

R2 configured as NTP client (without authentication) to synchronize from R1.

Synchronization verified after convergence.

![R2 NTP Status](08-r2-ntp-client-status.png)

---

## Manual Time Override Test

Manually changed the router time for testing purposes:

```
clock set 11:45:00 15 March 2020
```

After enabling NTP, the manual time was automatically overridden.

![Manual Time Set](09-r1-manual-time-set.png)

---

## Timezone Configuration

Configured timezone:

```
clock timezone PST -8
```

![Timezone Configured](10-r1-timezone-configured.png)

---

## Impact Analysis on R2

Observed downstream synchronization behavior after changes on R1.

R2 automatically adjusted its time once R1 re-synchronized with the NTP source.

![R2 After Changes](11-r2-time-after-r1-changes.png)

---

## Key Cybersecurity Takeaways

- Accurate timestamps are essential for security monitoring and log integrity.  
- NTP authentication prevents rogue or malicious time sources.  
- Manual clock changes are overridden when synchronization resumes.  
- Hierarchical NTP design improves internal reliability.  
- Time integrity directly impacts forensic accuracy and incident investigations.  

---

## Skills Demonstrated

- Cisco Router CLI configuration  
- NTP authentication and trust configuration  
- Time synchronization validation  
- Network hierarchy implementation  
- Log and timestamp integrity testing  
- Operational troubleshooting and verification  
