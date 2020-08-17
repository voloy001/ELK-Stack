# ELK-Stack
Deployment of containers using Ansible and Docker, Filebeat, and ELK stack on a server
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Red Team Resource Group and ELK Stack](https://github.com/voloy001/ELK-Stack/blob/master/Images/UNIT%2013%20DIAGRAM%20(2).jpg?raw=true) 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _playbook.yml_ file may be used to install only certain pieces of it, such as Filebeat.

  - _elk.yml_

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _available_, in addition to restricting _Access into_ to the network.
- _Load balancers protect data and virtual machine availability, therefore mitigating the risk of a DDoS attack. It protects all machines from a high influx of traffic at once that could potentially take down the machines. The advantage of a jumpbox is that it is a pivot server. Meaning you can pivot to other servers. It provides an added layer of security to the network. It also provides administrative security._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system logs.

-  _Filebeat watches for _System Logs_


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.  


| Name     | Function        | IP Address | Operating System  |
|----------|---------------  |------------|------------------ |
| Jump Box | Gateway         | 10.0.0.4   | Linux/Ubuntu 18.04|
| Web-1    |Web Server/DVWA  | 10.0.0.5   | Linux/Ubuntu 18.04|
| Web-2    |Web Server/DVWA  | 10.0.0.6   | Linux/Ubuntu 18.04|
| ELK-VM   |Log Server       | 10.1.0.4   | Linux/Ubuntu 18.04|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
98.210.215.230 My Home IP Address

Machines within the network can only be accessed by _Jump-Box-Provisioner with Ansible + Docker_.

The Jump Box Provisioner Machine is allowed access to the Elk VM with Private IP 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | my local IP          |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             |
| ELK-VM   | No                  | My Local IP          |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage of automation configuration with ansible is that it allows configuration to be repeated an unlimited amount of times and reduces error.


The playbook implements the following tasks:
-The steps of the ELK installation play:
- ... 
- ...
 
•	...Increase virtual memory
•	...Install Docker
•	...Install Pythin3-pip a python package manager
•	...Install a Docker python module
•	...Download and Enable to the docker

 



The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 
![Docker PS] https://github.com/voloy001/ELK-Stack/blob/master/Screenshots/sudodockerps.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1 - 10.0.0.5, Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
-  Filebeat collects sys logs from web1 and web2. It is then sent to Elasticsearch to be indexed. Examples include, update to device drivers, and application errors.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _filebeat-configuration_file_ to ansible/files
- Update the _host_ file to include the ELK IP address
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? filebeat-configuration.yml , /etc/filebeat/filebeat.yml


- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Filebeat-playbook add line ‘hosts: Elk’


- Which URL do you navigate to in order to check that the ELK server is running? 

http://[elk.ip]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- ssh azadmin@JumpboxPublicIP
- Ssh key-gen
-curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > filebeat-configuration.yml
- Sudo su
- Docker start focused_noyce
- Docker attach focused_noyce
- Nano filebeat-configuration.yml
- Nano elk.yml
- Nano filebeat.yml
- Ansible-playbook install-elk.yml
- Ansible-playbook filebeat.yml
