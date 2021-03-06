# ELK-Stack-Project
Penn Cybersecurity Bootcamp Project 1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[TODO: Update the path with the name of your diagram] (Images/diagram_filename.png)
		
		ELK-Stack-Project/Diagrams/JSS ELK Stack Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-ELK.yml file may be used to install only certain pieces of it, such as Filebeat.
- _TODO: Enter the playbook file._
		
		/etc/ansible/playbooks/install-ELK.yml
	
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
		
		Load balancers protect system availability by shifting traffic.
		A jump box provides a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system controls.
- _TODO: What does Filebeat watch for?_
		
		Filebeat monitors for changes in information on the file system.
		
- _TODO: What does Metricbeat record?_
		
		Metricbeat collects metrics from the operating system and services running.		

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address  | Operating System |
|----------|----------|-------------|------------------|
| Jump Box | Gateway  | 13.64.96.95 | Linux            |
| Web-1    | Server   | 10.1.0.5    | Linux            |
| Web-2    | Server   | 10.1.0.12   | Linux            |
| Web-3    | Server   | 10.1.0.14   | Linux            |
| ELK-1    | Server   | 10.2.0.5    | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
		
		JSS PC Public IP Address

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
		
		Jump-Box-Provisioner 13.64.96.95

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 69.139.83.112/32     |
| Web-1    | No                  | 13.64.96.95          |
| Web-2    | No                  | 13.64.96.95          |
| Web-3    | No                  | 13.64.96.95          |
| ELK-1    | No                  | 13.64.96.95          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
		
		Ansible is capable of configuring multiple VMs from a single playbook.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
		
		Installed docker.io
		Installed python-pip
		Installed docker
		Command to increase VM memory to run ELK container
		Starts ELK container on system boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[TODO: Update the path with the name of your screenshot of docker ps output] (Images/docker_ps_output.png)
		
		ELK-Stack-Project/Ansible/Images/ELK-1 docker ps.png
		
### Target Machines & Beats

This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
		
		Web-1 10.1.0.5
		Web-2 10.1.0.12
		Web-3 10.1.0.14
		
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
		
		Filebeat
		Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
		
		Filebeat monitors and collects logs at specific locations.
		Metricbeat periodically collects running service and operating system metrics.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
		
		/etc/ansible/playbooks/filebeat-configuration.yml
		/etc/ansible/playbooks/metricbeat-configuration.yml
		
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
		
		Update the /etc/ansible/host file to include webserver and ELK IP addresses
		
- _Which URL do you navigate to in order to check that the ELK server is running?
		
		http://20.80.41.168:5601/app/kibana#/home
		
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
		
		ansible-playbook filebeat-playbook.yml
		ansible-playbook metricbeat-playbook.yml
