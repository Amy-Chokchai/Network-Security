## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network diagram](Images/Azure_network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - Ansible Paybook File

  ![Playbook](Ansible/ansible_config.png) 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secured, in addition to restricting access to the network.
- Load Balancer protects applications from emerging threats by authenticating user access and controling traffics that get redistributed to the servers within the network. And Jump Box is used to access and manage devices in a saparate security zone. This system benefits high level network security, restricting access control, as well as increasing network redundency. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system security.
- Filebeat monitors log data files and collects log events.
- Metricbeat records statistical data from the system or servers.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    |          | 10.0.0.5   | Linux            |
| Web 2    |          | 10.0.0.6   | Linux            |
| ELK      |          | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Load Balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 20.211.177.174

Machines within the network can only be accessed by Jump Box.
- Web-1 and Web-2

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4             |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible automation allows the system to operate consistntly and sufficiently. It also helps to prevent human error.

The playbook implements the following tasks:
- Install docker.io, installing containerization software that allows you to run and manage your containers.
- Install python3-pip, installing a package-management system written in Python used to install and manage oftware packages
- Install docker python module, installing Python library for the Docker engine to run the containers.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screenshot](Diagrams/Screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4 and 10.0.0.5
- Filebeat and Metricbeat are fully installed

These Beats allow us to collect the following information from each machine:
- Filebeat collects log events: user logon events, failed access attempts, service starts and stops, and up time.
- Metricbeat collects system metrics from webservers, data usage, memory usage and drive space usage.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to etc/ansible.
- Update the host file to include ELK server.
- Run the playbook, and navigate to http://[20.58.179.218]:5601/app/kibana to check that the installation worked as expected.



_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

### Linux commands
 
Downloading filebeat configuration file
- curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb >> /etc/ansible/filebeat-config.yml

Running filebeat
- /etc/ansible# ansible-playbook filebeat-playbook.yml
