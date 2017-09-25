# Ansible Provisioning Test Bed

This is repository to use and test ansible provisioning

## Installation

1) [Install ansible](https://docs.ansible.com/ansible/latest/intro_installation.html), at least version 2.0
2) [Install vagrant](https://www.vagrantup.com/downloads.html)
3) Check out this repository
4) Run `vagrant up --provision` (and then `vagrant destroy`) once to ensure that everything is fetched properly

## Usage

You can provision a virtual machine (VM) using vagrant just by running

    vagrant up --provision

Shutting down the VM again:

    vagrant halt

You can also provision external systems just like the VM is provisioned by
running the provisioning file for a dedicated inventory:

    ansible-playbook -i ansible/<inventory> ansible/provision.yml

