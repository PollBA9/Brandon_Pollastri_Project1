## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Diagram/Diagram_Large.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the **.yml** file may be used to install only certain pieces of it, such as Filebeat.

  - **Use the ansible-playbooks [install-elk.yml](https://github.com/PollBA9/Brandon_Pollastri_Project1/blob/main/Ansible/install-elk.yml) and the 	[filebeat-playbook.yml](https://github.com/PollBA9/Brandon_Pollastri_Project1/blob/main/Ansible/Playbook/filebeat-playbook.yml), as these are required to create and setup the Elk-Server.**

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

- The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

- Load balancing ensures that the application will be highly **available**, in addition to restricting **access** to the network.

- **Load Balancer adds to the availability of security in regards to the CIA Triad.**

- **The advantage of a JumpBox is setting up a beginning point for starting Administrative Tasks. This sets the JumpBox as a "Secure Admin Workstation" or SAW for short. All Administrators conducting any Administrative Tasks will be required to connect to the JumpBox aka SAW before perfoming any task.**

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **logs** and system **traffic**.
- **Filebeat watches out for log files plus locations, and collects log events.**
- **Metricbeat records metric & statistical data from the operating system, and from services running on the server.**

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Docker-AE| 10.0.0.5   | Linux            |
| Web-2    | Docker-AE| 10.0.0.6   | Linux            |
| Elk-VM   | Elk      | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the **JumpBox** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
- **Personal IP Address**

Machines within the network can only be accessed by **SSH**.
- **The only machines that are able to connect to the Elk-VM (10.1.0.4) is via the Jumpbox (10.0.0.4) VM from the private IP, which pushes through the Web-1 (10.0.0.5) and Web-2 (10.0.0.6) VMs.**

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses             |
|----------|---------------------|----------------------------------|
| Jump Box | No                  | Personal IP Address              |
| Web-1    | No                  | 10.0.0.4                         |
| Web-2    | No                  | 10.0.0.4                         |
| Elk-VM   | No                  | 10.0.0.5, 10.0.0.6 & Personal IP | 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- **The advantages of automating config through Ansible is it's ease of use and learning. In the use of Playbooks' you are able to configure multiple Machines through the use of a single command, after setting up the initial configuration.**

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- **Create a New VM for Elk' give it a simple name. Make note of the Private IP (10.1.0.4) and the Public IP (52.243.80.18), you will need the Private IP to SSH into the VM and the Public IP to connect to the Kibana Portal (HTTP Site) to view all Metric logs.**
- 
- **Download and Configure the elk docker container "In the hosts.conf you will need to add a new group [elkservers] and the Private IP (10.0.0.11) to the group. Then you need to create a new ansible-playbook (elk.yml) that will download, install, configures the "Elk-Server" to map the following ports [5601,9200,5044], and starts the container.**
- 
- **Launch and expose the container "After installing and starting the new container. You can verify that the container is up and running by SSHing into the container from your JumpBox (SAW). Once you are in the [Elk-Server] run the command [sudo docker ps]**
- **Create new Inbound Security Rules to allow Ports: 5601 and 9200 "The Inbound Security Rules should allow access from your Personal Network."**
- **Open a new browser and type in the [Public IP:5601] to access the Kibana Portal Site.**

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
