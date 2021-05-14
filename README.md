# Project13_JA
# Cyber Security Work and Projects
The files in this repository were used to configure the network depicted below.

![Project diagram](/diagrams/Project_Diagram.JPG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
Load balancer also help mitigate DOS attacks.  Advantages of using a jumpbox is that you are fanning In through a single node, which forces all traffic
throught that single node. Easier to monitor one connection than multiple.

Integrating an ELK server allows users to easily monitor system logs for any  the vulnerable VMs 
 What does Filebeat watch for? Filebeat  helps generate and organize log files to send to Logstash and Elasticsearch. It collects file system logs  including
those that have changed. 
 What does Metricbeat record? Metricbeat periodically collect metrics from the operating system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     | DVWA     | 10.0.0.7   | Linux            |
| Web2     | DVWA     | 10.0.0.8   | Linux            |
| Web3     | DVWA     | 10.0.0.10  | Linux            |
| DVWA_VM3 | DVWA     | 10.1.0.4   | Linux            |
| DVWA_VM4 | DVWA     | 10.1.0.5   | Linux            |
| ELK-VM1  | ELK      | 10.2.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 Public IP : 108.21.59.191 

Machines within the network can only be accessed by Jump box.
 THe jump box can also access the ELK machine. The IP address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |  Yes                | 108.21.59.191        |
| Web 1    |  No                 | 1.0.0.4              |
| Web 2    |  No                 | 1.0.0.4              |
| Web 3    |  No                 | 1.0.0.4              |
| DVWA_VM3 |  No                 | 1.0.0.4              |
| DVWA_VM4 |  No                 | 1.0.0.4              |
| ELK-VM1  |  Yes                | 108.21.59.191        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it's quicker and easier to setup and/or destroy. 


The playbook implements the following tasks:
- Download .deb
- Install using dpkg 
- Copy Configuration files
- Run command filebeat modules enable system
- Run command filebeat setup
- Run command service filebeat start 



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.7, 10.0.0.8, 10.0.0.10, 10.1.0.4, 10.1.0.5

We have installed the following Beats on these machines:
10.0.0.7, 10.0.0.8, 10.0.0.10, 10.1.0.4, 10.1.0.5

These Beats allow us to collect the following information from each machine:
- Filebeats will collect logs
- Metricbeats will collect metric data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/files/.
- Update the config file to include elk machine IP 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

FAQ
- Which file is the playbook? All playbooks are under /Project13_JA/ansible/playbooks. Copy it to your provisioner ansible.
- Which file do you update to make Ansible run the playbook on a specific machine? You have to update the config files to specify which machine to run the playbook to.
-    How do I specify which machine to install the ELK server on versus which to install Filebeat on? Each one has its own seperate playbook to run.
- Which URL do you navigate to in order to check that the ELK server is running? your Public Facing ELK IP address:port. Example:  http://[your.VM.IP]:5601/app/kibana. 
