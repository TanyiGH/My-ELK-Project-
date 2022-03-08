## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/TanyiGH/My-ELK-Project-/blob/main/DIAGRAMS/My%20LexVM-ELK%20Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

----
### Playbook Files
  
  - [Elk-Installation Playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/elk.yml)
  - [Metricbeat-playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/playbook.yml)
  - [Filebeat-playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/Filebeat_Installation_Playbook.yml)
  - [DVWA-Web-Install-playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/my-playbook.yml)

----

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

----

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting authentication to the network.

- **What aspect of security do load balancers protect?**

_Distributed Denial-Of-Service (DDOS) Attacks_. 

**What is the advantage of a jump box?**

_A jump box accesses and manages all the devices in a different zone of security. It spans two different security zones and enables a controlled means of access between them_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system and system authentication.

- **What does Filebeat watch for?**

_Filebeat is used to forward and centralize log data. It monitors the log specified  files or locations, collects log events, and forwards them either to Elasticsearch or Logstash for indexing._

- **What does Metricbeat record?**

_Metricbeat records metrics and statistics collected from the system and services running on the server._

The configuration details of each machine may be found below.

| Name     | Function          | IP Address               | Operating System |
|----------|-------------------|------------------------- |------------------|
| Jump Box |Gateway            | 10.0.0.1/ 40.83.190.244  | Linux            |
| Web-1    |Web                | 10.0.0.9/40.83.145.12    | Linux            |
| Web-2    |Web                | 10.0.0.8/40.83.145.12    | Linux            |
| Elk      |Monitoring         | 10.1.0.5/20.114.192.64   | Linux            |

----

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 40.83.145.12
- 10.0.0.9
- 10.1.0.5
- 20.114.192.64

**Whitelisted IP addresses**

- My current Public IP is 69.138.246.12

_Machines within the network can only be accessed by my Jumpbox ansible container.

- **Which machine did you allow to access your ELK VM? What was its IP address?**
- Web-1 
- Ip address 10.0.0.9

_My Jumpbox through the ansible container, Jumpbox IP is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name                   | Publicly Accessible | Allowed IP Addresses        |
|------------------------|---------------------|-----------------------------|
| Jump Box               | Yes                 | 10.0.0.4 / 40.83.190.244    |
| Load Balancer          | No                  | 40.83.145.12                |
| Web-1                  | No                  | 10.0.0.9                    |
| LexVM ELK Server       | No                  | 10.1.0.5 / 20.114.192.64    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-  It is time saving, reduces errors and bugs and faciliatates the use of infrastructure as code

The playbook implements the following tasks:
- 
- ... Install docker
- ... Download the image
- ... Run sudo docker ps to view running containers
- ... Run sudo docker start eloquent_mayer
- ... Run sudo docker attach eloquent_mayer
- ... Run cd /etc/ansible
- ... finally run ls to view 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](https://github.com/TanyiGH/My-ELK-Project-/blob/main/Screenshots/Elk%20-%20Docker%20PS.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.8
- 10.0.0.9

We have installed the following Beats on these machines:
- 
- filebeat-7.4.0-amd64.deb
- metricbeat-7.6.1-amd64.deb

These Beats allow us to collect the following information from each machine:
- 
- Filebeat collects log events like audit logs, depreciation logs, gc logs, server logs and slow logs. It then forwards them either to Elasticsearch or Logstash for indexing.
For example, 
- Metricbeat records metrics and statistics collected from the system and services running on the server.
For example, 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the config file to include... remote user
- Run the playbook, and navigate to Kibana Dashboard for Metric or Filebeat to check that the installation worked as expected.

**Answer the following questions to fill in the blanks:**

- _Which file is the playbook? Where do you copy it?_
  - [Elk-Installation Playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/elk.yml)
  - [Metricbeat-playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/playbook.yml)
  - [Filebeat-playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/Filebeat_Installation_Playbook.yml)
  - [DVWA-Web-Install-playbook](https://github.com/TanyiGH/My-ELK-Project-/blob/main/ANSIBLE/my-playbook.yml)
  
  Copied to /etc/ansible
  
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- The /etc/ansible/host file

- _Which URL do you navigate to in order to check that the ELK server is running?

http://PUBLIC-IP/Kibana/app

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- azadmin@40.83.190.244
- sudo docker container list -a
- sudo docker ps 
- sudo docker start eloquent_mayer
- sudo docker attach eloquent_mayer
- cd /etc/ansible
- ls
