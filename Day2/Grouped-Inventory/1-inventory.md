# Ansible .inventory
 it can be written in two formats. **inventory.ini** or **Yaml**. 
This folder usually contains:

- `ansible.cfg`: The main configuration file for Ansible
- `hosts`: The default static inventory file
- `roles/`: A directory to organize reusable role definitions

![Inventory Screenshot](3.PNG)


# 📝 Edit the Inventory File
To manage your nodes, you need to edit the Ansible hosts file on the control node and add a group with the public IP addresses of the managed nodes.

Navigate to the hosts file:

       sudo vi /etc/ansible/hosts
       [production]
       slave1 ansible_host=35.154.228.102
       slave2 ansible_host=65.2.80.252


* production: This is the group name of your managed nodes.

* slave1 and slave2: These are the hostnames for the nodes.

* ansible_host: Specifies the public IP address to connect to for each node.