# 1. Enabling UFW (Uncomplicated Firewall) 
1. Checking the status of Ufw 

**Command:**
sudo ufw status

Status:
![status:inactive](./images%205/sudo%20ufw%20status%20inactive.png)

2. Before enabling UFW we need to make sure our connection to ssh is allowed using the following command:
sudo ufw allow 22/tcp

It is important to allow traffic through port 22 before enabling UFW because port 22 is used by SSH which is the protocol that allows remote login and management of the server.

**Allowing port 22:** 

![port 22](./images%205/sudo%20ufw%2022.png)

3. Allowing other specific connections like 80 and 443 using same command like port 22:

sudo ufw allow 80

sudo ufw allow 443

![port 80,443](./images%205/sudo%20ufw%2080%20443.png)