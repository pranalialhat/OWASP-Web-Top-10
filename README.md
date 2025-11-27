# OWASP-Web-Top-10
A complete hands-on lab setup for practicing OWASP Web Application Security Top 10 vulnerabilities using DVWA and bWAPP on Kali Linux with Docker.

🧩 Introduction
This project provides a safe and isolated environment to practice real-world web security attacks following the OWASP Web Top 10 list.
Using Docker, you can run vulnerable applications like DVWA and bWAPP without affecting your main system.

⭐ Why This Lab?
- 100% safe environment
- Perfect for beginners & security learners
- Learn common vulnerabilities practically
- Does not require VirtualBox / VMware
- Easy to run, reset, and destroy

🛠 Tools & Technologies
- Kali Linux
- Docker
- DVWA (Damn Vulnerable Web App)
- bWAPP (Buggy Web Application)
- Browser (Firefox/Chrome)

📌 Prerequisites
Make sure your Kali Linux is updated:
>> sudo apt update && sudo apt upgrade -y

🔧 1. Install Docker on Kali Linux

>> sudo apt update
>> sudo apt install docker.io -y
>> sudo systemctl enable --now docker

Verify installation:
>> docker --version

🔐 2. Fix Docker Permissions

(Add your user to the docker group so you don't need sudo)

>> sudo groupadd docker 2>/dev/null
>> sudo usermod -aG docker $USER
>> newgrp docker

Confirm Docker works without sudo:
>> docker ps

📥 3. Pull Vulnerable Web Applications
Pull DVWA
>> docker pull vulnerables/web-dvwa

Pull bWAPP
>> docker pull raesene/bwapp

▶️ 4. Run DVWA
>> docker run -d -p 8080:80 vulnerables/web-dvwa

Check container:
>> docker ps

▶️ 5. Run bWAPP
>> docker run -d -p 9001:80 raesene/bwapp

Check container:
>> docker ps

🌐 6. Access the Applications
🔸 DVWA
URL:
http://localhost:8080

Login:
Username: admin
Password: password

If database error → click Create / Reset Database. (This option is displayed when you access the url for the first time)

🔸 bWAPP
URL:
http://localhost:9001

Login:
Username: bee
Password: bug
Set Security Level → Low for easier testing.

🧪 7. Test Vulnerabilities
✔ SQL Injection (DVWA)
Go to:
DVWA → SQL Injection

Payload:
1' OR '1'='1

✔ Reflected XSS (bWAPP)
Go to:
Cross-Site Scripting → Reflected

Payload:
"><script>alert(1)</script>

🛑 8. Manage/Stop Containers
List running containers:
>> docker ps

Stop a container:
>> docker stop <container-id>

Remove a container:
>> docker rm <container-id>

Remove images:
>> docker rmi vulnerables/web-dvwa
>> docker rmi raesene/bwapp

🩹 9. Troubleshooting
❌ Permission denied:
Run:
>> sudo usermod -aG docker $USER
>> newgrp docker

❌ Port already in use:
>> sudo lsof -i :8080
>> sudo kill <pid>

❌ DVWA database error:
Click Create / Reset Database.

🧭 10. What You Can Practice
This lab helps you practice all OWASP Top 10 categories:

✔ Injection :
SQLi, Command Injection

✔ Broken Authentication :
Weak passwords, session issues

✔ Sensitive Data Exposure :
Insecure transport, weak crypto

✔ XML External Entities (XXE) :
Test XML processing flaws

✔ Broken Access Control :
IDOR, privilege escalation

✔ Security Misconfigurations :
Headers, debug mode, default creds

✔ Cross-Site Scripting (XSS) :
Reflected, Stored, DOM XSS

✔ Insecure Deserialization :
PHP object injection (bWAPP)

✔ Using Components with Vulnerabilities :
Outdated libraries

✔ Insufficient Logging & Monitoring :
Test logs + audit failures

✅ Conclusion
This setup gives you a complete, safe, and practical environment to master OWASP Web Top 10 vulnerabilities.
Whether you're preparing for a Security Analyst role, Pentesting, Bug Bounty, or DevSecOps — this lab is a perfect starting point.
