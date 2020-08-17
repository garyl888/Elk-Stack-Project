## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Update the path with the name of your diagram](Images/diagram_filename.png)
(https://github.com/garyl888/Elk-Stack-Project/blob/master/ProjectFINALDRAWING.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _install-elk3.yml_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly __available_, in addition to restricting _access____ to the network.
- What aspect of security do load balancers protect? __Load balancers allow access to the web server Virtual Machines. They provide "Redundancy" so that if one server goes down the other will be able to compensate for the traffic. Thus it protects the Availability aspect of the CIA Triad.__

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __files__ and __system__logs.
- What does Filebeat watch for? _system logs_
- What does Metricbeat record?  _system metrics_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                   | Function        | IP Address | Operating System     |
|------------------------|-----------------|------------|----------------------|
| Jump Box               | Gateway         |10.0.0.4    | Linux (Ubuntu 18.04) |
| Web-1                  | WebServer/dvwa  |10.0.0.7    | Linux (Ubuntu 18.04) |
| Web-2                  | WebServer/dvwa  |10.0.0.8    | Linux (Ubuntu 18.04) |
| Project-vMachine1      | Elk Log server  |10.1.0.4    | Linux (Ubuntu 18.04) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __Jump Box__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _My_HOME_IPAddress_98.199.XX.XX_

Machines within the network can only be accessed by _Jump Box with Ansible Docker_.
- Which machine did you allow to access your ELK VM? What was its IP address? _Jump-Box-Provisioner_ _10.0.0.4_

A summary of the access policies in place can be found in the table below.

| Name                | Publicly Accessible | Allowed IP Addresses |
|---------------------|---------------------|----------------------|
| Jump-Box-Provisioner| Yes                 | 98.199.XX.XX         |
| Web-1               | No                  | 10.0.0.4             |
| Web-2               | No                  | 10.0.0.4             |
| Project-vMachine1   | No                  | 98.199.XX.XX         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_Allows_you_to_configure_various_machines_all_from_one_place._

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install.docker.io
- Install python3-pip
- Install docker module
- Increase Virtual Memory
- Download and launch a docker container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)
(https://github.com/garyl888/Elk-Stack-Project/blob/master/Images/docker%20ps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web-1&Web-2_10.0.0.7&10.0.0.8_

We have installed the following Beats on these machines:
- _Filebeat_

These Beats allow us to collect the following information from each machine:
- _Filebeat monitors the log files. It collects logs events and forwards them to either Elasticsearch or Logstash_

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _filebeat-config_file_to_the_ansible_file__.
- Update the _Host_ file to include Elk-IP.
- Run the playbook, and navigate to _Kibana_ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? _filebeat-configuration.yml_copied_to_/etc/ansible/files
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_filebeat-configuration_Placed_the_private_ip_on_the_Elk_section_
- Which URL do you navigate to in order to check that the ELK server is running? http://104.43.129.211:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._