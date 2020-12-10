## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Images/'AzureCloudDiagramELKStack.png')

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the artemis.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system resources.


The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |   |
|----------|------------|------------|------------------|---|
| Jump-Box | Gateway    | 10.0.0.4   | Ubuntu Linux     |   |
| WEB-1    | Web Server | 10.0.0.7   | Ubuntu Linux     |   |
| Web-2    | Web Server | 10.0.0.8   | Ubuntu Linux     |   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Azure Load Balancer can accept connections from the Internet. Access to this machine is only allowed from the public facing IP address of the workstation at my home. 


Machines within the network can only be accessed via SSH from the Jump-Box machine with IP 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.7 10.0.0.8    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because in a redundant environment, configurations on all of the clustered machines need to match.

The playbook implements the following tasks:
- Install Docker
- Install Python & pip3
- Downloads & launches DVWA Container
- Enables the Docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
WEB-1, WEB-2

We have installed the following Beats on these machines:
FileBeat, MetricBeat


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the artemis.yml file to /etc/ansible.
- Update the artemis.cfg file to include the IP address of the ELK VM.
- Run the playbook, and navigate to 10.1.0.4:5601 to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._