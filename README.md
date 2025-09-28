# ITSecGames Vulnerability Assessment Reports

**Target:** [www.itsecgames.com](http://www.itsecgames.com) (IP: 31.3.96.40)  
**Assessment Date:** 27th September 2025  
**Prepared By:** Malagundla Manjunath  

---

## 📄 Overview

This repository contains the **comprehensive vulnerability assessment reports** for the web application and server hosted at www.itsecgames.com.  
The assessment was performed using the following tools:  

- **Nmap 7.94SVN** – Port scanning, service version detection, OS detection, and default NSE scripts.  
- **OWASP ZAP (D-2025-09-18)** – Passive and active web application scanning, spidering, fuzzing, and security analysis.  
- **testssl.sh** – SSL/TLS protocol, cipher, and certificate assessment.  

The purpose of this project is **educational**, aimed at understanding common vulnerabilities and mitigation strategies.

---

## 🛠 Tools & Techniques

| Tool        | Purpose                                                     |
|------------|-------------------------------------------------------------|
| Nmap       | Identify open ports, running services, OS detection, and vulnerabilities. |
| OWASP ZAP  | Scan web application for security misconfigurations, headers, and potential XSS/CSRF issues. |
| testssl.sh | Check SSL/TLS protocol support, weak ciphers, certificate issues, and related vulnerabilities. |

---

## ⚠️ Key Findings

### 1. SSH (Port 22)
- **Service:** OpenSSH 6.7p1  
- **Risk:** Critical  
- **Issues:** Multiple CVEs (CVE-2015-5600, CVE-2016-1908, CVE-2023-38408)  
- **Mitigation:** Update OpenSSH, enforce key-based authentication, disable root login, use firewall rules.  

### 2. HTTP / HTTPS (Port 80/443)
- **Service:** Apache httpd  
- **Risk:** Medium-High  
- **Issues:** Missing security headers (HSTS, CSP, X-Frame-Options), outdated modules.  
- **Mitigation:** Upgrade Apache, enable security modules, configure headers, limit HTTP methods.  

### 3. SSL/TLS
- **Issues:** Expired self-signed certificate, TLS 1.0/1.1 enabled, missing TLS 1.3, weak CBC ciphers.  
- **Mitigation:** Renew certificate from a trusted CA, enable TLS 1.3, disable weak ciphers, implement HSTS.  

### 4. Web Application Security (OWASP ZAP)
- Missing CSP, SRI, anti-clickjacking headers.  
- Permissions-Policy and Cross-Origin headers not set.  
- Mitigation includes adding all relevant security headers and testing for content integrity.

