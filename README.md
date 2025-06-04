# HTB-Redeemer-Redis-Enumeration

# HTB Redeemer – Redis Exploitation & Flag Extraction

## 📝 Project Summary
This penetration testing project targets the "Redeemer" machine from Hack The Box, focusing on exploitation of a misconfigured Redis server running on port 6379. By connecting to the Redis instance via `redis-cli`, database contents were dumped, and the flag was retrieved directly from memory.

## 📌 Objective
Explore Redis enumeration and extraction of data from an exposed, unauthenticated Redis server.

## 🔧 Tools Used
- Nmap  
- redis-cli  
- Linux terminal tools (`ping`, `curl`, etc.)

## 🧪 Methodology

### 1. Enumeration
- Verified target was online via `ping`
- Scanned ports using:

  nmap -sV <target_IP>

Found open Redis port: 6379

2. Accessing Redis
Installed Redis tools:

sudo apt install redis-tools

Connected to Redis

redis-cli -h <target_IP>

3. Redis Enumeration

Viewed server info:

info

Selected DB index:

select 0

Listed Keys

keys *

Retrieved flag:

get <key>

🚨 Vulnerability Identified
Misconfigured Redis: Open to unauthenticated access over the internet

Impact: Anyone could extract data directly from the Redis key-value store

✅ Recommendations
Bind Redis to localhost or secure it with authentication

Enable Redis ACLs for key-based access control

Use firewall rules or VPN tunneling for remote access
