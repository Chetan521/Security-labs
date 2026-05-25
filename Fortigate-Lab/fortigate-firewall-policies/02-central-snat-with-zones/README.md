
# 02 — Central SNAT with Zones

## 🎯 Objective
Use Central NAT to translate INSIDE → OUTSIDE traffic.

---

## 🛠️ Step‑by‑Step

### **Step 1 — Enable Central NAT**
System → Feature Visibility → Central NAT → ON

### **Step 2 — Create SNAT Rule**
Policy & Objects → Central SNAT → Create New

- **Source:**fw3wan1(23.1.2.0/24) 
- **Destination:** all  
- **Outgoing Interface:** OUTSIDE  
- **Translated Address:** Use Outgoing Interface IP  

---

## 💻 CLI Equivalent

```
config firewall central-snat-map
    edit 1
        set srcaddr "fw3wan1"
        set dstaddr "all"
        set protocol 0
        set outbound-interface "OUTSIDE"
        set nat-ippool "wan-ip"
    next
end
```

---

## 🔍 Verification
- SNAT logs  
- Public IP check  
- Policy hit count  

---

## ✅ Conclusion
Central NAT gives full control over outbound IP translation.
