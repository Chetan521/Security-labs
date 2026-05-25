
# 03 — Inside → DMZ Policy (Zone‑Based)

## 🎯 Objective
Allow restricted access from INSIDE zone to DMZ servers.

---

## 🛠️ Step‑by‑Step

### **Step 1 — Create DMZ Interface**
Network → Interfaces → Create New  
- Address: 10.10.10.1/24  
- Role: DMZ  

### **Step 2 — Add DMZ to a Zone (Optional)**
Network → Zones → Create New  
- Name: DMZ  
- Add interface: dmz  

### **Step 3 — Create Policy**
- Incoming: INSIDE  
- Outgoing: DMZ  
- Service: HTTP/HTTPS/SSH  
- NAT: OFF  

---

## 💻 CLI Equivalent

```
config firewall policy
    edit 10
        set name "INSIDE-to-DMZ"
        set srcintf "INSIDE"
        set dstintf "DMZ"
        set srcaddr "all"
        set dstaddr "DMZ-Servers"
        set action accept
        set service "HTTP" "HTTPS"
        set schedule "always"
    next
end
```

---

## 🔍 Verification
- Access server  
- Logs show INSIDE → DMZ  
- Blocked ports appear in logs  

---

## ✅ Conclusion
This lab demonstrates segmentation using zones.
