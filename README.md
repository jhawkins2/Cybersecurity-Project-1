# Cybersecurity-Project-1
The files in this repository were used to configure the network depicted below.

These files have been tested and used to create an ELK Stack Deployment on the Azure environment. These files can be used to either remodel the entire deployment pictured above or specific files that can be used as a guide to install components of the deployment such as filebeats.

This document contains the following:
Description of the Topology
Access Policies
ELK Configuration
Machines being Monitored
How to use Ansible
# Description of the Topolgy
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulneable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load balancers protect the servers from a denial of service attack. A load balancers purpose is to distribute traffic among the servers. One positive note from using the Jump Box is that it has great protection from Virtual Machines and public exposure.
Integrating an ELK server allows easier monitoring and access to the vulnerable VMs for changes to log files and system performance.
The configuration details of each machine may be found below:
╔══════════╦══════════╦════════════╦════════════════════╦══╦══╦══╗
║ name     ║ Function ║ IP address ║ Operating System   ║  ║  ║  ║
╠══════════╬══════════╬════════════╬════════════════════╬══╬══╬══╣
║ Jumpbox  ║ Gateway  ║ 10.0.1.4   ║ Linux ubuntu 18.04 ║  ║  ║  ║
╠══════════╬══════════╬════════════╬════════════════════╬══╬══╬══╣
║ DVWA-VM1 ║ VM       ║ 10.0.1.7   ║ Linux ubuntu 18.04 ║  ║  ║  ║
╠══════════╬══════════╬════════════╬════════════════════╬══╬══╬══╣
║ DVWA-VM2 ║ VM       ║ 10.0.1.8   ║ Linux ubuntu 18.04 ║  ║  ║  ║
╠══════════╬══════════╬════════════╬════════════════════╬══╬══╬══╣
║ DVWA-VM3 ║ VM       ║ 10.0.1.9   ║ Linux ubuntu 18.04 ║  ║  ║  ║
╠══════════╬══════════╬════════════╬════════════════════╬══╬══╬══╣
║ DVWA-VM4 ║ VM       ║ 10.0.1.10  ║ Linux ubuntu 18.04 ║  ║  ║  ║
╠══════════╬══════════╬════════════╬════════════════════╬══╬══╬══╣
║ ELK VM   ║ VM       ║ 10.0.1.12  ║ Linux ubuntu 18.04 ║  ║  ║  ║
╚══════════╩══════════╩════════════╩════════════════════╩══╩══╩══╝
# Access Policies
The machines on the internal network are not exposed to the public internet
Only the Jumpbox machine can accept connections from the internet. Access to this machine is only allowed for the following IP addresses: 72.84.225.151
Machines within the network can only be accessed by port 22: 10.0.1.4
A summary of the access policies in place can be found in the table below.
╔═══════════╦════╦═══════════════╗
║ Jump Box  ║ no ║ 72.84.225.151 ║
╠═══════════╬════╬═══════════════╣
║ DVWA-VMs  ║ no ║ 10.0.1.4      ║
╠═══════════╬════╬═══════════════╣
║ ELK Stack ║ no ║ 10.0.1.4      ║
╚═══════════╩════╩═══════════════╝
# Elk Configuration
Ansible was used to automate configuration of the ELK machine. 
Ansible can be run from the command line and will ensure our provisioning scripts run identically.
The playbook implements the following tasks:
Change the memory on the ELK VM
Install docker.io
Install python-pip
Install docker python module
Download and launch a docker elk stack
The following screenshot displays the result of running docker ps after successfullt configuring the ELK instance
