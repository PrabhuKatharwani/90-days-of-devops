# Week 1: DevOps Networking Fundamentals - 90 Days Challenge 🚀

Welcome to my **90 Days of DevOps Challenge**! I'm excited to share my learning journey with you all. This week, I'm diving deep into networking fundamentals, which form the backbone of any DevOps career.

## Why Networking Matters in DevOps? 🤔

Before we jump into the technical stuff, let me tell you why networking is crucial for DevOps professionals:
- **Server Communication**: Applications need to talk to each other across different servers
- **Cloud Infrastructure**: Understanding how data flows in cloud environments
- **Troubleshooting**: When things break, networking knowledge helps you find the root cause
- **Security**: Knowing how data travels helps you secure it better

---

## 1: Understanding OSI & TCP/IP Models 📚

### What are these models?
Think of these models as **blueprints** that explain how data travels from your computer to another computer over the internet.

### OSI Model (7 Layers)
The OSI model has 7 layers.

| Layer | Name     | Real-World Example          | What It Does                        |
|-------|----------|-----------------------------|-------------------------------------|
| 7 | Application  | Web browser, Email apps     | Where you interact (Gmail, Chrome)  |
| 6 | Presentation | HTTPS encryption, JPEG      | Encrypts and formats data           |
| 5 | Session      | Login sessions, Video calls | Manages conversations between apps  |
| 4 | Transport    | TCP, UDP                    | Ensures data arrives safely         |        
| 3 | Network      | IP addresses, Routers       | Finds the best path to destination  |
| 2 | Data Link    | Ethernet, WiFi              | Handles local network communication |
| 1 | Physical     | Cables, WiFi signals        | The actual wires and signals        |
![6262390676863961180](https://github.com/user-attachments/assets/369ce97f-d048-4e54-851b-d1f6338658e2)



### TCP/IP Model (4 Layers)
This is what the internet actually uses! It's simpler than OSI:

| Layer | Name       | Purpose                                  |
|-------|------------|------------------------------------------|
| 4 | Application    | Combines OSI layers 5-7 (HTTP, FTP, SSH) |
| 3 | Transport      | Same as OSI layer 4 (TCP, UDP)           |
| 2 | Internet       | Same as OSI layer 3 (IP routing)         |
| 1 | Network Access | Combines OSI layers 1-2 (Ethernet, WiFi) |

### Real-World Example: Loading a Website
When you type `google.com` in your browser:
1. **Application Layer**: Browser sends HTTP request
2. **Transport Layer**: TCP breaks data into packets
3. **Internet Layer**: IP finds route to Google's servers
4. **Network Access Layer**: WiFi/Ethernet sends the actual signals

---

## 2: Essential DevOps Protocols & Ports 🔌

Here are the protocols every DevOps engineer should know:

### Web Protocols
- **HTTP (Port 80)**: Regular websites
- **HTTPS (Port 443)**: Secure websites (with SSL/TLS)
- **WebSocket (Port 80/443)**: Real-time communication

### File Transfer
- **FTP (Port 21)**: File transfer (not secure)
- **SFTP (Port 22)**: Secure file transfer
- **SCP (Port 22)**: Secure copy over SSH

### Remote Access
- **SSH (Port 22)**: Secure shell for server access
- **Telnet (Port 23)**: Unsecure remote access (avoid!)
- **RDP (Port 3389)**: Windows remote desktop

### DNS & Email
- **DNS (Port 53)**: Translates domain names to IP addresses
- **SMTP (Port 25/587)**: Sending emails
- **POP3 (Port 110)**: Receiving emails
- **IMAP (Port 143)**: Email synchronization

### Database Connections
- **MySQL (Port 3306)**: Popular database
- **PostgreSQL (Port 5432)**: Another popular database
- **MongoDB (Port 27017)**: NoSQL database
- **Redis (Port 6379)**: In-memory database

**DevOps Tip**: Always use secure protocols in production (HTTPS instead of HTTP, SFTP instead of FTP)!

---

## 3: AWS EC2 & Security Groups 🛡️

### What are Security Groups?
Think of Security Groups as **virtual firewalls** for your EC2 instances. They control what traffic can come in (inbound) and go out (outbound).

### Step-by-Step Guide to Create EC2 with Security Groups

#### Step 1: Launch EC2 Instance
1. Go to AWS Console → EC2 Dashboard
2. Click "Launch Instance"
3. Choose Amazon Linux 2 (Free Tier eligible)
4. Select t2.micro (Free Tier)
5. Configure Security Group (next steps)

#### Step 2: Configure Security Group
1. **Create New Security Group**: Give it a meaningful name like "web-server-sg"
2. **Add Inbound Rules**:
   - SSH (Port 22) from your IP address only
   - HTTP (Port 80) from anywhere (0.0.0.0/0)
   - HTTPS (Port 443) from anywhere (0.0.0.0/0)
3. **Outbound Rules**: Leave default (allows all outbound traffic)

#### Step 3: Security Best Practices
- **Never allow SSH (22) from 0.0.0.0/0** - only from your IP
- **Use HTTPS (443) instead of HTTP (80)** when possible
- **Follow least privilege principle** - only open ports you actually need
- **Use descriptive names** for security groups

### Common Security Group Rules for DevOps:
```
Web Server:
- Inbound: HTTP (80), HTTPS (443) from anywhere
- Inbound: SSH (22) from your IP only

Database Server:
- Inbound: MySQL (3306) from web server security group only
- Inbound: SSH (22) from your IP only

Load Balancer:
- Inbound: HTTP (80), HTTPS (443) from anywhere
- Outbound: HTTP (80) to web server security group
```

---

## 4: Essential Networking Commands Cheat Sheet 🛠️

Here are the networking commands every DevOps engineer should master:

### 1. ping - Test Connectivity
```bash
# Check if a server is reachable
ping google.com
ping 8.8.8.8

# Send only 4 packets
ping -c 4 google.com
```
**Use Case**: Check if your server can reach the internet or another server.

### 2. traceroute/tracert - Trace Network Path
```bash
# Linux/Mac
traceroute google.com

# Windows
tracert google.com
```
**Use Case**: Find where network packets are getting stuck or taking too long.

### 3. netstat - Network Statistics
```bash
# Show all active connections
netstat -a

# Show listening ports
netstat -l

# Show with process names
netstat -p
```
**Use Case**: Check what ports your applications are using and if they're accessible.

### 4. curl - Make HTTP Requests
```bash
# Basic GET request
curl https://api.github.com

# Check response headers
curl -I https://google.com
```
**Use Case**: Test APIs, download files, check if web servers are responding.

### 5. dig/nslookup - DNS Lookup
```bash
# Find IP address of domain
dig google.com
nslookup google.com

# Check specific DNS record
dig google.com MX
dig google.com A
```
**Use Case**: Troubleshoot DNS issues, verify domain configurations.

### Pro Tips for Using These Commands:
- **Use curl to test your APIs** before deploying
- **Use netstat to check if your application is listening** on the right port
- **Use ping to verify connectivity** between servers
- **Use dig to troubleshoot DNS issues** in production

---

## Week 1 Summary & Next Steps 📋

This week I learned:
✅ OSI and TCP/IP models and their real-world applications  
✅ Essential protocols and ports for DevOps workflows  
✅ AWS EC2 Security Groups for cloud security  
✅ Networking commands for troubleshooting  

### Key Takeaways:
1. **Networking is everywhere** in DevOps - from server communication to cloud security
2. **Security Groups are crucial** for protecting cloud resources
3. **Command-line tools** are essential for troubleshooting network issues
4. **Understanding protocols** helps in designing better architectures

### Next Week Preview:
Week 2 will focus on **Linux Command Line & System Administration**. I'll be diving into file systems, user management, and automation scripts.

---

## Connect With Me 🤝

I'm documenting my entire 90-day DevOps journey! Follow along:
- **Twitter/X**: Share your thoughts and networking tips
- **LinkedIn**: Connect for professional networking
- **GitHub**: Check out my practice projects and code

**What networking challenge would you like to see me tackle next? Drop a comment below!**

---

*week 1 of 90 Days DevOps Challenge complete! 🎉*

**#DevOps #90DaysOfDevOps #Networking #AWS #CloudSecurity #TechLearning #DevOpsCommunity #LearnInPublic #CloudComputing #TechCareer #DevOpsChallenge #NetworkingBasics #AWSLearning #DevOpsSkills #TechJourney #OpenSource #CloudNative #InfrastructureAsCode #SysAdmin #TechEducation**
