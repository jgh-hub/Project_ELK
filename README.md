# Project_ELK
    ## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.


/etc/ansible/ELKserver.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secured, in addition to restricting access to the network.

A Load Balancer protects the system from DDOS attacks by redirecting attach traffic. 
The advantage of a jumpbox is to give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.

Filebeat watches for any changed information in the file system.

Metricbeat take the collection's metric and statistics and ships the info to the specific output. 
The configuration details of each machine may be found below.

| Name      | Function | IP Address | Operating System |
|-----------|----------|------------|------------------|
| Jump Box  | Gateway  | 10.0.0.5   | Linux            |
| DVMA-VM2  | Server   | 10.0.0.14  | Linux            |
| Web-1     | Server   | 10.0.0.12  | Linux            |
| ELKserver | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Public IP address  73.106.148.21
Machines within the network can only be accessed by Private IP address.


Jump Box Provisioner VM 10.0.0.5
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |  73.106.148.21       |
| DVWA-VMA2| No                  |  10.0.0.14           |
| ELKserver| No                  |  10.1.0.4            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

Main advantage is that you can put commands into multiple servers from a single playbooks.
The playbook implements the following tasks:

- Install: Docker.io
- Install: docker
- Command: sysctl -w vm.max map_count= 262144
- Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

DVMA-VM1 10.0.0.13
DVMA-VM2 10.0.0.14
We have installed the following Beats on these machines:

Filebeats and Metricbeats
These Beats allow us to collect the following information from each machine:

 
Filebeat collects the changes.
Metricbeat collects metrics and statistics.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy newly yml file to the edited yml file.
- Update the yml file to include all recent updates
- Run the playbook, and navigate to ping to check that the installation worked as expected.


- _Which file is the playbook? Where do you copy it?_
- /etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
-  Edit the /etc/ansible/host file to add ip addresses' of webservers and elkserver.
-  _Which URL do you navigate to in order to check that the ELK server is running?_
 www.publicip:5601 (Kibana)
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
    ansible-playbook filebeat-playbook.yml
