## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/chidobootcamp/Project/blob/main/Diagrams/Homework%20File%20Cloud%20Security.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.

  (Playbooks/install-elk.yml) (Playbooks/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable with the increased traffic. The load balancer will also help keep the network's availability high with routing traffic evenly across the networks.

What aspect of security do load balancers protect? This protects the servers from becoming overloaded, as well as protecting against Distributed Denial of Service (DDoS) attacks.

What is the advantage of a jump box?	When a jump box is used, its hidden benefit is that any tools in place for the SAN (Storage Area Network) system are maintained on that single system. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the uptime and system logs.
- _TODO: What does Filebeat watch for?	Filebeat is deployed on VMs in the environment in order to monitor all the system logs that are being generated.	
- _TODO: What does Metricbeat record?	Metricbeat records uptime and system metrics based around the VMs perfomrace related to the CPU, memory, etc.

If the pool of VMs begins to grow adding a load balancer will ensure that the application will be highly stable with the increased traffic. The load balancer will also help keep the network's availability high with routing traffic evenly across the networks.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

|        Name        |  Function  | IP Address | Operating System |
|:------------------:|:----------:|:----------:|:----------------:|
| JumpBoxProvisioner |   Gateway  |  10.0.0.4  |       Linux      |
|     DVWA-Web-1     |   Server   |  10.0.0.5  |       Linux      |
|     DVWA-Web-2     |   Server   |  10.0.0.6  |       Linux      |
|     DVWA-Web-3     |   Server   |  10.0.0.7  |       Linux      |
|       ELK-VM       | Elk Server |  10.1.0.4  |       Linux      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
52.242.99.88

Machines within the network can only be accessed by Secure Shell (SSH).
The Jump Box has acces to the ELK ELK VM. Its IP address is 52.234.179.117

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses |
|--------------------|---------------------|----------------------|
| JumpBoxProvisioner |         Yes         |        Home IP       |
|        Web-1       |          No         |       10.0.0.4       |
|        Web-2       |          No         |       10.0.0.4       |
|        Web-3       |          No         |       10.0.0.4       |
|       Elk-VM       |          No         |   Home IP, 10.0.0.4  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage of automating configuration with Ansible is that it can speed up the deployment of a virtual network.

The playbook implements the following tasks:

    Install docker.io
    Install python-pip
    Install docker module pip
    Increase virtual memory
    Downlaod and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

C:\Users\User\Desktop\Projects\Diagrams\docker_ps_output

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.5), Web-2 (10.0.0.6) and Web-3 (10.0.0.7)

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to collect changes made
- It also allows us to determine when the changes were made

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the host file to include the webservers and elk vm...

/etc/ansible/host should include:

[webservers]

[ip address] ansible_python_interpreter=/usr/bin/python3

[ip address] ansible_python_interpreter=/usr/bin/python3

[elk]

[ip address] ansible_python_interpreter=/usr/bin/python3

- Run the playbook, and SSH into the elk vm, then run docker ps to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? The yaml(.yml) file is the playbook.
- _Which file do you update to make Ansible run the playbook on a specific machine? You must update the hosts file. 
	How do I specify which machine to install the ELK server on versus which to install Filebeat on? In the heading of the yaml file next to host, specify which machine you want to perform the install using the category you listed the machine on in the hosts file.
- _Which URL do you navigate to in order to check that the ELK server is running?   http://[your.ELK-VM.External.IP]:5601/app/kibana
