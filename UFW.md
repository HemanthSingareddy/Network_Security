# I. Enabling UFW (Uncomplicated Firewall) 

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

To check all the network statistics we use command sudo ss -tuln. tuln checks all TCP,UDP, and Listening, n displays addresses in numeric form and Socket Statistics(ss) is a command line utility for checking network statistics.
![sudo ss -tuln](./images%205/sudo%20ss%20-tuln.png)
 
 The above command line lists all the ports active in the Vm machine. I have found a port which I'm unsure of i.e. port 631.
 Using the command: sudo lsof -i :portNumber we can check the specific service.
 ![sudo lsof -i :portNumber](./images%205/sudo%20port%20631.png)

 4. Enabling UFW using command: sudo ufw status and
 5. let's check the status of UFW now using command: sudo ufw status
 
 ![ufw enable](./images%205/sudo%20ufw%20enable.png)
  Let's check the status of UFW now using command: sudo ufw status
 
6. Important ports that should be allowed through in UfW for a web server are port 80 and port 443 because:

Port 80 is used for regular, unencrypted web like like HTTP.

Port 443 is used for secure, encrypted web traffic like HTTPS.

7. By uing the command; sudo ufw status verbose we can see that the firewall is properly configured only necessary services are open.

![sudo verbose](./images%205/verbose%20status.png)

8. To block someone's ip address from using the UFW we can use the **command: sudo ufw deny <ip address>**. Below image shows an example on how to block someone's ip address.
![sudo ufw deny](./images%205/sudo%20ufw%20deny.png)

9. To allow someone's ip address to a specific port we can use the **command: sudo ufw allow from <ip address> to any <port no>**. 

Port 587 is used for SMTP (Simple Mail Transfer Protocol) submission. It is the default port for sending outgoing mails from an email client to a mail server.
![sudo ufw allow](./images%205/sudo%20ufw%20allow.png)

10. Let's check all the rules by checking the status once more
![sudo verbose](./images%205/verbose%20status.png)

# II. Enable UFW Logging
1. Before checking the logs. Let's make sure that UFW logging is enabled. to enable logging we can use the **command: sudo ufw logging on** and 2. setting logging level to high using the **command: sudo ufw logging high** and by setting the logging level to high it includes all blocked packets and connection information.
![sudo ufw logging on](./images%205/sudo%20ufw%20logging.png)

3. Usually a typical UFW log entry looks like the following image given below. This information is useful for monitoring, troubleshooting and securing the network. Each entry in the UFW log entry provides valuable data about the traffic that was blocked or allowed which helps in identifying any suspicious activity or configuration issues in the UFW.

4. The UFW logs are stored in /var/log/ufw.log. Using the following command we can view our own logs in our VM: **sudo tail -f /var/log/ufw.log** The -f options allows you to monitor the log in real time.
![log Entry](./images%205/sudo%20tail.png)

5. To check specific entries like denied traffic or allowed traffic we can use the grep command. Grep is a powerful command-line utility in Linux used to search for specific text patterns within files or command outputs.

- For denied traffic: sudo grep 'DENY' /var/log/ufw.log
- For allowed traffic: sudo grep 'ALLOW' /var/log/ufw.log
![grep command](./images%205/sudo%20grep%20deny%20allow.png)

There was no output for DENY because no unauthorized or blocked connection attempts occured during the logging period.