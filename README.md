# Provision Docker Swarm with Ansible on EC2 Instances

These playbooks allow you to provision Docker Swarm on Amazon EC2.

There are two playbooks:
* `provision_ec2_playbook.yml` which is responsible for creating the security groups and two EC2 instances.
* `provision_swarm_playbook.yml` which is responsible of installing Docker on the two EC2 instances, initializing one as Manager and the other as Worker.

### Requirements
   * Ansible 2.9+
   * python >= 2.7
   * boto
   * awscli
   * ec2.py

### What it does
Running the playbook `provision_ec2_playbook.yml` does the following:

1. Creates the 'swarm' Security Group, allowing swarm members to communicate between themselves and allow ssh
1. Creates 2 EC2 Instances; the first one with the SwarmType Tags as 'manager' and the second one with the SwarmType Tags as 'worker'

Running the playbook `provision_swarm_playbook.yml` does the following:

1. Install docker, python-pip, jsondiff and pyyaml making sure that docker is started and enabled at boot on both instances
1. In the EC2 instance declared as 'manager', it initializes the Swarm
1. In the EC2 instance declared as 'worker' it joins the worker to the swarm