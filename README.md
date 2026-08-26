# Cerberus XSS

**Cerberus XSS** by **Sudeepa Wanigarathne** is an advanced XSS testing tool for ethical hackers, penetration testers, and bug bounty hunters. It includes a wide range of features such as web crawling, WAF bypass techniques, DOM-based XSS detection, and blind XSS payload logging. With a rich terminal UI, Cerberus XSS offers interactive menus, progress bars, and detailed vulnerability reports.

> ⚠️ **Ethical Use Only:** Always test with proper authorization. Unauthorized testing is illegal.

---

## ✨ Features

- **Web Crawling** – Spiders websites to identify forms, parameters, and potential injection points.  
- **Payload Injection** – Tests a wide variety of XSS payloads, including obfuscated and encoded versions.  
- **WAF Bypass** – Evades web application firewalls with techniques like comment injection, case alteration, nested encoding, etc.  
- **DOM-based XSS Detection** – Identifies DOM sinks for client-side JavaScript-based XSS vulnerabilities.  
- **Blind XSS Logging** – Sends out-of-band payloads and logs callbacks from vulnerable targets.  
- **Rich Terminal UI** – Uses the [Rich](https://github.com/Textualize/rich) library for colorful output, interactive prompts, and detailed tables.  
- **Session Persistence** – Resume scans without losing progress.  
- **Proxy Support** – Supports HTTP proxies like Burp Suite for traffic inspection.  

---

## 🛠️ Installation

<img width="1640" height="921" alt="image" src="https://github.com/user-attachments/assets/2cbe8191-44e6-4773-abbd-9cd052e3a3b3" />

Cerberus XSS is built for **Kali Linux** and uses a Python virtual environment.

```bash
# 1. Update Kali Linux
sudo apt update && sudo apt upgrade -y

# 2. Install Python & Venv
sudo apt install python3 python3-pip python3-venv -y

# 3. Clone the Repository
git clone https://github.com/CerberusMrXi/cerberus_xss.git
cd cerberus_xss

# 4. Set Up Virtual Environment
python3 -m venv venv
source venv/bin/activate

# 5. Install Dependenciespython cerberus_xss.py
pip install -r requirements.txt

# 6. All Done
python cerberus_xss.py


