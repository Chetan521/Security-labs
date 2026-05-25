# FortiGate Firewall Policies Lab

## Objective

Configure FortiGate firewall policies to control and secure traffic between internal and external networks.

---

## Lab Environment

| Device | Role | IP Address |
|--------|------|-------------|
| FortiGate VM | Firewall | 192.168.48.138 |
| Ubuntu Server | Attacker Machine | 192.168.1.10 |
| Ubuntu Server | Internal Server | 192.168.1.20 |
| VPCS | Internal Client | 192.168.1.30 |

---

## Technologies Used

- FortiGate VM
- VMware Workstation
- Kali Linux
- Ubuntu Server
- Windows 10

---

## Network Topology

(Add topology screenshot here)

Example:

![Topology](screenshots/topology.png)

---

## Firewall Policy Configuration

### Step 1 — Configure Interfaces

Configured:
- WAN Interface
- LAN Interface

### Step 2 — Create Address Objects

Created address objects for:
- Internal LAN
- Ubuntu Server
- Windows Client

### Step 3 — Configure Firewall Policies

Created policies to:

- Allow internal users internet access
- Block unauthorized inbound traffic
- Restrict traffic between internal systems
- Log all denied connections

---

## Security Rules Implemented

| Policy | Action |
|--------|--------|
| LAN → WAN | Allow |
| WAN → LAN | Deny |
| Kali → Ubuntu | Restricted |
| Internal DNS | Allow |

---

## Verification Testing

Performed connectivity and filtering tests:

### Ping Test

```bash
ping 192.168.1.20
```

### Port Scan Test

```bash
nmap 192.168.1.20
```

---

## Results

- Internal users successfully accessed the internet
- Unauthorized inbound traffic was blocked
- Firewall logs captured denied traffic attempts
- Security policies worked as expected

---

## Screenshots

(Add screenshots below)

Example:

![Firewall Policy](screenshots/firewall-policy.png)

![Traffic Logs](screenshots/traffic-logs.png)

---

## Lessons Learned

- Firewall policy order is critical
- Deny-by-default improves security
- Logging helps identify suspicious traffic
- Network segmentation reduces attack surface

---

## Skills Demonstrated

- FortiGate administration
- Firewall policy management
- Network traffic filtering
- Security monitoring
- Basic threat detection
