# Cybersecurity
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Cybersecurity/Docker_and_Ansible/ansible/elk_playbook1.PNG
Cybersecurity/Docker_and_Ansible/ansible/elk_playbook2.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the elk_install.ymal file may be used to install only certain pieces of it, such as Filebeat.

Cybersecurity/Docker_and_Ansible/ansible/elk_install.ymal

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?
-The load balancer helps manage the load of the webservers
-The advantage of a jump box is that its a centralized station/vm that can help manage the rest of the network/vms. Reducing the possible entry points a threat actor can use.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system information.
What does Filebeat watch for?
-Filebeat monitors the log data of the server and saves the various events.
What does Metricbeat record?
-Collects metric data of the server.

The configuration details of each machine may be found below.

| Name                 | Function  | IP Address | Operating System |
|----------------------|-----------|------------|------------------|
| Jump-Box-Provisioner | Gateway   | 10.0.0.4   | Linux            |
| Web-1                | Webserver | 10.0.0.5   | Linux            |
| Web-2                | Webserver | 10.0.0.6   | Linux            |
| Web-3                | Webserver | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
40.85.145.4

Machines within the network can only be accessed by ssh from the Docker container on the Jump-Box-Provisioner.
Jump-Box-Provisioner 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-because it can help speed the process of the configuring hundreds(or more) machines/VMs at once instead of manually configuring each machine/VM seperately.

The playbook implements the following tasks:
-Download/install Docker.io/python3-pip
-Increase the virtual memory
-launch the ELK docker container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
-Cybersecurity/Docker_and_Ansible/ansible/elk_playbook1.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-Web-1:10.0.0.5
-Web-2:10.0.0.6
-Web-3:10.0.0.8

We have installed the following Beats on these machines:
-ELK-VM:10.1.0.4

These Beats allow us to collect the following information from each machine:
-Various data, filebeat monitors and collects log data while metricbeat collects metrics from the OS and system

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the my_playbook.ymal file to /etc/ansible directory.
- Update the ansible.cfg file to include the remote user (should look like "remote_user=VM_Username"
- Run the playbook, and navigate to VM to check that the installation worked as expected.

Which file is the playbook? Where do you copy it?
the elk_install.ymal and my_playbook.ymal, you copy it into your /etc/ansible directory
-Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
The 'host' file should be updated to have the machine names/IPs. You specify the 'elk' group with the elk VM ip
-Which URL do you navigate to in order to check that the ELK server is running?
http://<elkVM public ip>:5601/app/kibana

