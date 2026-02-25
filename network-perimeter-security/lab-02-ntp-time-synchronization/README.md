# Lab 02 – NTP Time Synchronization (Cisco Packet Tracer)

## Objective
Design and configure a secure Network Time Protocol (NTP) infrastructure including authentication, hierarchical synchronization, and time validation across routers.

---

## 🖥️ Network Topology

![Topology](01-topology-diagram.png)

---

## 🔧 Initial IP Configuration (R1)

![R1 IP Configuration](02-r1-ip-configuration.png)

---

## ⏱️ NTP Server Configuration

Configured NTP server with authentication key.

![NTP Server Configuration](03-ntp-server-configuration.png)

---

## 🔐 R1 as NTP Client (Authenticated)

R1 configured to synchronize with NTP server using authentication.

![R1 NTP Client](04-r1-ntp-client-authentication.png)

---

## ✅ NTP Synchronization Status

Verification using:

```
show ntp status
show clock
```

![R1 NTP Status](05-r1-ntp-status-synchronized.png)

---

## ⚠️ Clock Drift Demonstration

After modifying the NTP server time, synchronization mismatch is observed.

![Clock Out of Sync](06-r1-clock-out-of-sync.png)

---

## 🏢 R1 as NTP Master

Enabled R1 to act as NTP master for internal devices.

Command used:

```
ntp master
```

![R1 NTP Master](07-r1-ntp-master-enabled.png)

---

## 🌐 R2 Synchronizing from R1

R2 configured as NTP client without authentication.

![R2 NTP Status](08-r2-ntp-client-status.png)

---

## 🕒 Manual Time Override (Test)

Manually set time:

```
clock set 11:45:00 15 March 2020
```

![Manual Time Set](09-r1-manual-time-set.png)

---

## 🌎 Timezone Configuration

Command:

```
clock timezone PST -8
```

![Timezone Configured](10-r1-timezone-configured.png)

---

## 🔁 Synchronization Impact on R2

Observed how changes on R1 affected downstream synchronization.

![R2 After Changes](11-r2-time-after-r1-changes.png)

---

## 🔎 Key Cybersecurity Takeaways

- Accurate timestamps are critical for SIEM and log correlation
- Time synchronization prevents forensic timeline inconsistencies
- NTP authentication mitigates rogue time server attacks
- Hierarchical NTP design improves internal network reliability
- Manual clock changes are overridden once synchronization resumes

---

## 🎯 Skills Demonstrated

- Cisco Router CLI configuration
- NTP authentication
- Network hierarchy implementation
- Log accuracy validation
- Operational time integrity management
