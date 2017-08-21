# Ansible Provisioning Test Bed

This is repository to use and test ansible provisioning

## Usage

You can provision a virtual machine (VM) using vagrant just by running

    vagrant up --provision

You can also provision external systems just like the VM is provisioned by
running the provisioning file for a dedicated inventory:

    ansible-playbook -i ansible/<inventory> ansible/provision.yml

