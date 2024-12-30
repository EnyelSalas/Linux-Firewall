# Linux-Firewall

# Firewalld Command Examples Cheat Sheet

This **Firewalld Command Examples Cheat Sheet** provides a categorized overview of essential `firewalld-cmd` commands for managing and securing your Linux firewall. It is a handy reference for configuring zones, managing services, creating custom rules, and troubleshooting firewalld settings.

---

## Table of Contents
1. [Basic Commands](#basic-commands)
2. [Zone Management](#zone-management)
3. [Service Management](#service-management)
4. [Custom Rules](#custom-rules)
5. [Monitoring and Troubleshooting](#monitoring-and-troubleshooting)

---

## Basic Commands
- **Check Firewalld Version**: 
  ```bash
  firewall-cmd --version
Install Firewalld:

Fedora: Preinstalled
RHEL/CentOS:
sudo yum install firewalld

Debian/Ubuntu:
sudo apt-get update
sudo apt-get install firewalld

Arch Linux:
sudo pacman -S firewalld

Start Firewalld:
sudo systemctl start firewalld

Enable Firewalld at Boot:
sudo systemctl enable firewalld
Zone Management


Show Current Zone:
sudo firewall-cmd --get-active-zones

Change Zone of an Interface:
sudo firewall-cmd --change-interface=<interface_name> --zone=<zone_name> --permanent

Create a New Zone:
sudo firewall-cmd --new-zone=<zone_name> --permanent

Associate Interface with a Zone:
sudo firewall-cmd --zone=<zone_name> --add-interface=<interface_name> --permanent

List All Zones:
sudo firewall-cmd --get-zones

Set Default Zone:
sudo firewall-cmd --set-default-zone=<zone_name>
Service Management

List Available Services:
sudo firewall-cmd --get-services

Allow a Service:
sudo firewall-cmd --zone=<zone_name> --add-service=<service_name> --permanent

Deny a Service:
sudo firewall-cmd --zone=<zone_name> --remove-service=<service_name> --permanent

List Active Service Rules:
sudo firewall-cmd --zone=<zone_name> --list-services
Custom Rules

Open a Specific Port:
sudo firewall-cmd --zone=<zone_name> --add-port=<port_number>/<protocol> --permanent

Remove a Port Rule:
sudo firewall-cmd --zone=<zone_name> --remove-port=<port_number>/<protocol> --permanent

Add a Custom Rule:
sudo firewall-cmd --zone=<zone_name> --add-rich-rule='rule family="ipv4" source address="<ip_address>" port port="<port_number>" protocol="<protocol>" accept'

Hide a Port:
sudo firewall-cmd --zone=<zone_name> --add-rich-rule='rule family="ipv4" source address="0.0.0.0/0" port port="<port_number>" protocol="<protocol>" drop'
Monitoring and Troubleshooting

Reload Firewalld Configuration:
sudo firewall-cmd --reload

Check Active Rules:
sudo firewall-cmd --list-all

Monitor Active Connections:
sudo firewall-cmd --list-connections

Enable Event Logging:
sudo firewall-cmd --set-log-denied=all

View Firewalld Logs:
sudo journalctl -u firewalld

Block an IP Address:
sudo firewall-cmd --zone=public --add-rich-rule='rule family="ipv4" source address="<ip_address>" drop'
