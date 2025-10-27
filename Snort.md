# Exploring Snort

In this lab I'll be installing and configuring Snort for my virtual machine. Let's check out the utilizaton of snort.

## System Update

Updating the system before installing and configuring snort.
![system update](./images%206/system%20update.png)

## Installing Snort

The command to install snort on the system is : sudo apt install snort -y

![Snort install](./images%206/snort%20install.png)

Snort will be installed to /etc/snort/ with the default configuration and rules.

To find the network interface we can use the command:

ip a

![ip a](./images%206/snort%20network%20interface.png)

With this information we can set the network interface to any network we want to monitor and the HOME_NET to define our home network.

## Configuring Snort

To customize the Snort configuration, first we need to open the main configuration file using command:

sudo nano /etc/snort/snort.conf

![configure snort](./images%206/configure%20snort.png)

As seen my Home_net network is any. We can customize the network range by using the command:

ipvar HOME_NET network range

## Update and Manage Snort Rules

Snort by default comes with community rules, but we can download and add additional rules for better threat detection.

![update snort](./images%206/update%20snort%20logs.png)
![manage snort](./images%206/manage%20snort%20logs.png)

We can also add our own rules in the local rule file by using the command:

sudo nano /etc/snort/rules/local.rules

Then, add custom rules like:

alert icmp any any -> any any (msg:"ICMP detected"; sid:1000001; rev:1;)

![custom rules](./images%206/custom%20rules.png)

Rules related to port scanning, SQL injection attempts sttod out and snort rules define how to detect specifc network events or attacks. 

## Testing Snort Configuration

After configuring the snort we can check if it is working properly or not by running the command:

sudo snort -T -c /etc/snort/snort.conf

![test snort](./images%206/Test%20snort.png)

After running the command, if the configuration is working properly it shows the message like this:
Snort successfully validated the configuration!

## Running Snort in IDS mode

Now we have installed and configured Snort we can run it in IDS mode to monitor traffic and we can also specify the interface to monitor like: eth0, enX0, etc. by using the command:

sudo snort -c /etc/snort/snort.conf -i eth0

![running snort](./images%206/running%20snort.png)

To exit the monitoring of network traffic and log alerts hit ctrl+c

## Viewing Snort Logs

Snort log alerts are all saved to /var/log/snort/ directory. It shows all the files saved of snort logs.

![viewing snort](./images%206/Logs.png)

The file snort.alert.fast.1.gz contains content which is compressed log data which is unreadable

## Running Snort as a Daemon

To run Snort in the background as a daemon, we can specify the interface to monitor like eth0, enX, etc. using the command:

sudo snort -D -c /etc/snort/snort.conf -i eth0

![daemon](./images%206/Daemon.png)

This command will keep snort running in the background monitoring the specified network.

To check other processes running in the system we can use the command:  top it will show snort running 

![top](./images%206/Daemon-1.png)

To stop the monitoring of snort running we can use the command:
ctrl+c.

In this lab we have went through the basics of snort and its configurations and how it monitors networt interfaces and logs.