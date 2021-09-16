# ELK-Stack-Demo
A demonstration of a functional ELK stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/networktopology.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook files may be used to install only certain pieces of it, such as Filebeat.



This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting unwanted access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system metrics.


The configuration details of each machine may be found below.

| Name                 | Function   | IP Address | Operating System   |
|----------------------|------------|------------|--------------------|
| Jump Box Provisioner | Gateway    | 10.0.0.4   | Linux Ubuntu 20.04 |
| Web 1                | Web Server | 10.0.0.5   | Linux Ubuntu 20.04 |
| Web 2                | Web Server | 10.0.0.6   | Linux Ubuntu 20.04 |
| ELK Machine          | ELK Stack  | 10.1.0.5   | Linux Ubuntu 20.04 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
76.232.10.10

Machines within the network can only be accessed by the Jump Box Provisioner

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | IP AddressAllowed IP Addresses |
|----------------------|---------------------|--------------------------------|
| Jump Box Provisioner | Yes                 | 10.0.0.5, 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for this configuration to be easily duplicated.

The playbook implements the following tasks:
- Increases the available memory for the VM
- Installs docker
- Installs python3
- Installs ELK container
- Ensures Docker enables on VM restart

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Diagrams/docker-ps

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web 1 10.0.0.5
Web 2 10.0.0.6

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat: monitors log data
Metricbeat: monitors metrics from system and services

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the [filebeat][metricbeat]-playbook.yml file to your Ansible control node.
- Update the ansible.cfg file to include your username on your Web-VM's.
- Run the playbook, and navigate to the public IP address of your ELK Machine to check that the installation worked as expected.
