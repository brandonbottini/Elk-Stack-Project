## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Images/https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Diagrams/Elk%20Stack%20done.drawio.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _Install-Elk: https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Ansible/Install-elk.yml_

  - _Host: https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Ansible/hosts_

  - _Ansible Configuration: https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Ansible/ansible.cfg_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _The security that a load balancer provides is it allows the network to distrubes traffic evenly. The jump box acts as an aduit for incoming traffic._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- _Filebeat watches for any any changes to the data on a system._
- _Metricbeat records system log information and monitors what services are run._

The configuration details of each machine may be found below.

| Name      | Function          | IP Address | Operating System |
|-----------|-------------------|------------|------------------|
| Jump Box  | Gateway           | 10.0.0.4   | Linux            |
| Web1      | Web Server        | 10.0.0.5   | Linux            |
| Web2      | Web Server        | 10.0.0.6   | Linux            |
| Elk Stack | Monitoring Server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
- Public IP address: Add whitelisted IP addresses

Machines within the network can only be accessed by ssh.
-: The machine that can access the ELK VM is through the jump-box. The private ip address of the jump-box is 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses     |
|---------------|---------------------|--------------------------|
| Jump Box      | Yes/No              | 10.0.0.4 and Personal IP |
| Web1          | No                  | 10.0.0.5                 |
| Web2          | No                  | 10.0.0.6                 |
| Elk-Stack     | Yes/No              | 10.1.0.4 and Personal IP |
| Load Balancer | Yes                 | 20.124.13.65             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _: The main advantage of using automating configuration with Ansible is that all the machines to be configurd in the same way._

The playbook _Install-Elk: https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Ansible/Install-elk.yml_ implements the following tasks:
- Sets maximum map count
- Install docker.io
- Install pip3
- Install Docker Module
- Download and launch Elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Images/Elk%20Stack%20Docker.png]

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 10.0.0.5
- Web2 10.0.0.6

We have installed the following Beats on these machines:

Filebeat [https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Ansible/filebeat-playbook.yml] and Metricbeat [https://github.com/brandonbottini/Files-from-Cyber-Security-Class/blob/main/Ansible/metricbeat-playbook.yml]

These Beats allow us to collect the following information from each machine:
- _Filebeat monitors logs on the machine and sends the data off to Elasticsearch. For example the filebeat would look at audit logs to relay these logs to the elk-stack machine._

- _Metricbeat captures metrics and statistics from the machines and send the data off to Elasticsearch. Metricbeat would look at the uptime of the system or the system logs._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/files.
- Update the /etc/ansible/hosts file to include the ip address of the webservers and the elk-stack. 
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
