
# 01 — Inside → Outside Internet Policy (Zone‑Based)

## 🎯 Objective
Allow LAN users (INSIDE zone) to access the internet through the OUTSIDE zone.

---

## 🗺️ Topology
- INSIDE zone = port3  
- OUTSIDE zone = port1
- VPCS → INSIDE → FortiGate → OUTSIDE → Internet

---

## 🛠️ Step‑by‑Step GUI Configuration

### **Step 1 — Verify Zones**
Network → Zones  
- INSIDE:  port3  
- OUTSIDE: port1  

### **Step 2 — Create Firewall Policy**
Policy & Objects → Firewall Policy → Create New

- **Name:** IN-OUT 
- **Incoming Interface:** INSIDE  
- **Outgoing Interface:** OUTSIDE  
- **Source:** Subnet_192.168  
- **Destination:** all  
- **Service:** ALL  
- **Action:** ACCEPT  
- **NAT:** (Central NAT will apply automatically)

### **Step 3 — Logging**
Enable:
- Log Allowed Traffic → All Sessions

---

## 💻 CLI Equivalent (Zone‑Based)

```
config firewall policy
    edit 1
        set name "IN-OUT"
        set srcintf "INSIDE"
        set dstintf "OUTSIDE"
        set srcaddr "Subnet_192.168"
        set dstaddr "all"
        set action accept
        set schedule "always"
        set service "ALL"
        set nat enable
    next
end
```

---

## 🔍 Verification
- Forward Traffic Logs show INSIDE → OUTSIDE  
- Policy Hit Count increases  
- PC can ping 8.8.8.8  
- PC can browse internet  

---

## ✅ Conclusion
This is the core zone‑based internet access policy used in enterprise networks.
