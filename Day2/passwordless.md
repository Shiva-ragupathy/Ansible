# Passwordless Authentication
Ansible is an agentless automation tool, meaning it does not require any agent software to be installed on the managed nodes. Instead, Ansible is installed only on the **control nodes**, which is the system from where you run Ansible commands. Instructions are provided using YAML-based playbooks or ad-hoc commands, and Ansible can handles **Managed nodes** by configuring services such as **Nginx** or **Apache2**.
 There are two main types of authentication used by Ansible to connect to remote nodes:
 - **SSH** key-based authentication (recommended for automation)
 - **Password-based authentication**.

 Let's Create a SSH key based authentication by using this command.

            ** ssh-keygen -t rsa (In managed-nodes)**
            ** cd .ssh/**
            ** ll**
            ** cat id_rsa.pub **

Copy this key and paste it in managed-nodes.

          **cd .ssh/**
          **ll**
          **vi authorized_keys**
          **ssh ubuntu@43.205.194.xxx (paste the SSH keys you copied from Ansible master node)**




