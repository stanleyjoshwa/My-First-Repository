# My-First-Repository
Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagrams/Project%201.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  Enter the playbook file.

Elk-install.yml
Filebeat-playbook.yml
Metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build

Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting malicious attacks to the network.
What aspect of security do load balancers protect? 
Protect applications from emerging threats
Authenticate User Access
Protect against DDoS attack
Simplify PCI compliance

What is the advantage of a jump box?
      Jump Box prevents all other VMs from being exposed to the public.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
What does Filebeat watch for? Log Files and collects log events including the ones that has been changed.

What does Metricbeat record? Collects or records Metrics and Statistics

The configuration details of each machine may be found below.

| Name              | Function              | IP Address  | Operating System |
|--------------------|-------------------------|-----------------|-------------------------
| CS Jump Box | Gateway               | 10.0.0.4      | Linux                     |
| Web 1             | Web Server          | 10.0.0.7      | Linux                     |
| Web 2             | Web Server          | 10.0.0.6      | Linux                     |
| Web 3             | Web Server          | 10.0.0.9      | Linux                     |
| ELK                | ELK   Server         | 10.1.0.4      | Linux                     |


Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Add whitelisted IP addresses 52.137.86.46

Machines within the network can only be accessed by SSH.
Which machine did you allow to access your ELK VM? My local Machine
What was its IP address? 52.137.86.46
| Name       | Publicly Accessible | Allowed IP Addresses    |
|---------------|---------------------------|---------------------------------|
| Jump Box | Yes                         | 52.137.86.46                  |
| Web 1       | No                          |                                        |
| Web 2       | No                          |                                        |
| Web 3       | No                          |                                        |
| ELK Server | Yes                       | 52.137.86.46                  |

Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because automation can improve the consistency and reliability of the environment, and saves time when configuring large numbers of servers.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
 
Install docker.io
Install python3-pip 
Install Docker module
Increase virtual memory.
download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![](Diagrams/Docker%20ps.png)




Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring

Web 1 IP: 10.0.0.7
Web 2 IP: 10.0.0.6
Web 3 IP: 10.0.0.9

We have installed the following Beats on these machines:
filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

Copy the provided `filebeat.yml` and `metricbeat.yml` into your Ansible VM's `/etc/ansible/files` directory

Update the config files to use the private IPs of ELK Server to the elasticsearch (line 1106)
 and the setup.kibana sections (line 1806). 

Run the playbook, and navigate to http://[52.242.124.19]:5601/app/kibana to check that the installation worked as expected.






Answer the following questions to fill in the blanks:_
Which file is the playbook? 

filebeat-playbook.yml
metricbeat-playbook.yml


Where do you copy it? /etc/ansible


Which file do you update to make Ansible run the playbook on a specific machine? 

Host file

How do I specify which machine to install the ELK server on versus which to install Filebeat on?

Hosts: elkserver

Host: webservers

Which URL do you navigate to in order to check that the ELK server is running?

http://[52.242.124.19]:5601/app/kibana
