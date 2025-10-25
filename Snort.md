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