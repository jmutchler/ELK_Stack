### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Elk_Stack/Diagrams/Diagram ELK Project.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  Elk_Stack/Ansible/

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network. The advantage of using the jump box is that only the jump box can access the Virtual network through ssh 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
 What does Filebeat watch for? Filebeat monitors the log files, collects log events, and forwards them to either Elasticsearch or Logstash for indexing
 What does Metricbeat record? Metricbeat takes metrics and statistics that it collects and ships them to the output you specify, such as Elasticsearch or Logstash

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name 	| Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.5   | Linux            |
| web1 	|web server | 10.0.0.9  | Linux            |
| web2 	|web server | 10.0.0.10 | Linux            |
| Elk-Stack|ELK server | 10.1.0.4  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from by home IP address

Machines within the network can only be accessed by accessing the Jump Box.
- I allowed my Jump Box to SSH into the ELK VM in the Ansible container the IP is 52.149.211.103

A summary of the access policies in place can be found in the table below.

| Name 	| Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes          	      | Home-IP              |
| web1     | no                 	|  10.0.0.5            |
| web2    	| no	                |  10.0.0.5             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because automating configurations with Ansible allows for quick and easy deployment. 


The playbook implements the following tasks:
Install docker-io
Install python3-pip
Install docker with pip
Increase System Memory
Download and launch docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Elk_Stack/Diagrams/docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.9
10.0.0.10

We have installed the following Beats on these machines:
ELK, Web1 and Web2

These Beats allow us to collect the following information from each machine:
Filebeat: Log events
Metricbeat: Metric and system statistics 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the playbook yml file to /etc/ansbile
- Update the host file to include webserver and ELK
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _The file for the playbook is in Ansible folder and copy to the files to /etc/ansible
- Need to edit the ansible hosts file to include your host name and IP addresses. To change the host machine that the playbook runs on you need to specify the host name in the playbook file at the beginning with hosts options.
- _Which URL do you navigate to in order to check that the ELK server is running?
 http://[your.ELK-VM.External.IP]:5601/app/kibana
