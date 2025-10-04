# Exploring Ubuntu Home Lab

This lab focuses on exploring the **network environment** of my Ubuntu virtual machine and identifying potential vulnerabilities. The goal is to understand how my server communicates on the network and ensure it is securely configured.

## 1. Identifying Network Interfaces and IP Addresses

**Command:**
ip a or ifconfig

**Purpose:**
ip a or ifconfig displays all network interfaces and their assignment IP addresses. This helps me identify which interfaces are active and how my VM connects to the network.

**Output:**
![ip a or ifconfig](./images/ip.png) 

## 2. Check Open Ports

**Command:**
sudo netstat -tuln or ss -tuln

**Purpose:**
sudo netstat -tuln or ss -tuln lists all open TCP or UDP ports to identify what services are listening on my system.

**Output:**
![sudo netstat -tuln or ss -tuln](./images/sudo%20netstat.png)