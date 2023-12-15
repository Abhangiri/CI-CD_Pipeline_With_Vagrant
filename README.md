
# CI/CD Pipeline with Vagrant

This repository contains configurations for setting up a CI/CD pipeline environment using Vagrant. The pipeline includes Jenkins, SonarQube, and Nexus running on separate virtual machines.



## Table of Contents


- [Prerequisites](#prerequisites)
- [Getting Started](#Getting-Started)
- [Project Structure](#project-structure)
- [Customization](#customization)
- [Troubleshooting](#troubleshooting)


## Prerequisites

Ensure you have the following tools installed:

- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/Abhangiri/CI-CD_Pipeline_With_Vagrant.git
   cd CI-CD_Pipeline_With_Vagrant


2. Start the virtual machines:

   `vagrant up`

3. Access the services:

- **Jenkins:** [http://10.3.20.11:8080](http://10.3.20.11:8080)
- **SonarQube:** [http://10.3.20.13:9000](http://10.3.20.13:9000)
- **Nexus:** [http://10.3.20.12:8081](http://10.3.20.12:8081)

4. Log in to Jenkins using the initial admin password found in the Jenkins VM at
 `/var/lib/jenkins/secrets/initialAdminPassword`.




## Project Structure



- **configurations:** Scripts for setting up Jenkins, Nexus, and SonarQube.
- **README.md:** This file with instructions and project details.
- **Vagrantfile:** Configuration for Vagrant, defining VMs, networks, and provisioning.



## Customization

- **Modify Configurations:** Update scripts in `configurations/*.sh` to suit your specific requirements.
- **Adjust VM Settings:** Modify the VM settings in the `servers` array within the `Vagrantfile`.
  - Add or remove VMs based on your needs.

  
## Troubleshooting


#### Slow Network Speed

If you encounter slow network speed during provisioning, you can try improving it by adding the following lines to the VirtualBox provider settings in the `Vagrantfile`:

```ruby
# fix for slow network speed issue
vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
