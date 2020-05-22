# Provision Docker Swarm with Ansible on EC2 Instances

These playbooks allow you to provision Docker Swarm on Amazon EC2.

There are two playbooks:
* `provision_ec2_playbook.yml` which is responsible for creating the security groups and two EC2 instances.
* `provision_swarm_playbook.yml` which is responsible of installing Docker on the two EC2 instances, initializing one as Manager and the other as Worker.