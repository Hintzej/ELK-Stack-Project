## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](hintzej/Network_Diagrams/Cloud Server Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting strain to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | Server   | 10.0.0.6   | Linux            |
| Web 2    | Server   | 10.0.0.7   | Linux            |
| Web 3    | Server   | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancing machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
98.33.219.231

Machines within the network can only be accessed by ssh from the jumpbox.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessable | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 98.33.219.231        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because future instances can be automatically created quickly without risk of human error

The playbook implements the following tasks:
- Install docker
- Install python3
- Install docker module
- Allocate virtual memory
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text][Images/docker_ps.png]

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web 1: 10.0.0.6
Web 2: 10.0.0.7
Web 3: 10.0.0.8

We have installed the following Beats on these machines:
Web 1: 10.0.0.6
Web 2: 10.0.0.7
Web 3: 10.0.0.8

These Beats allow us to collect the following information from each machine:
- Logs, processes ran, amount of traffic in bytes and number of visitors, etc

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ssh public key file to the new webserver.
- Update the /etc/ansible/hosts file to include the local ip address of the new webserver
- Run the playbook, and navigate to kibana to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?_
- filebeat-playbook.yml is the playbook and you run it to copy it to the webservers by running it.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- The /etc/ansible/hosts file. The playbook will run based on whether the system is under webservers or elk
- _Which URL do you navigate to in order to check that the ELK server is running?
- http://52.138.82.200:5601/app/kibana#/home
