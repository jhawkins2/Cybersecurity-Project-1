# Cybersecurity-Project-1
The files in this repository were used to configure the network depicted below.

https://mail.google.com/mail/u/0?ui=2&ik=9a7f9b75a1&attid=0.1.1&permmsgid=msg-f:1705037145093062844&th=17a9823ff21e40bc&view=fimg&sz=s0-l75-ft&attbid=ANGjdJ9uv0sbHTygNNiC6emDHjHy91xpO6WEtFa8TvPtiqyxy8-HgVRurcpBwlCK4tEQwGLi51et-qRK6q7mKemfTfipjxD4-J_9bEXSYp43GjpdzulwPRNs-czdhiU&disp=emb
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
╔══════════╦══════════╦════════════╦════════════════════
║ name     ║ Function ║ IP address ║ Operating System   
╠══════════╬══════════╬════════════╬════════════════════
║ Jumpbox  ║ Gateway  ║ 10.0.1.4   ║ Linux ubuntu 18.04 
╠══════════╬══════════╬════════════╬════════════════════
║ DVWA-VM1 ║ VM       ║ 10.0.1.7   ║ Linux ubuntu 18.04 
╠══════════╬══════════╬════════════╬════════════════════
║ DVWA-VM2 ║ VM       ║ 10.0.1.8   ║ Linux ubuntu 18.04 
╠══════════╬══════════╬════════════╬════════════════════
║ DVWA-VM3 ║ VM       ║ 10.0.1.9   ║ Linux ubuntu 18.04 
╠══════════╬══════════╬════════════╬════════════════════
║ DVWA-VM4 ║ VM       ║ 10.0.1.10  ║ Linux ubuntu 18.04 
╠══════════╬══════════╬════════════╬════════════════════
║ ELK VM   ║ VM       ║ 10.0.1.12  ║ Linux ubuntu 18.04
╚══════════╩══════════╩════════════╩════════════════════
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

# Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.1.7
10.0.1.8
10.0.1.9
10.0.1.10
We have installed the following beat on this machines:
filebeat-7.6.1-amd64.deb
This beat allows us to collect the following information from each machine:
Filebeat is used to send you log files to kibana. Filebeat monitors and collects log events on specified servers.
# Using the Playbook
In ordeer to use the playbook, you will need to have an ansible control mode already configured. 
SSH into the control node and follow the steps below:
Copy the Filebeat-configuration.yml file to the ELK VM.
Update the hosts file to include webservers 10.0.1.7, 10.0.1.8, 10.0.1.9, 10.0.1.10
Run the playbook, and navigate to Kibana to check that the installation worked as expected.
$ ansible-playbook filebeat-playbook.yml
