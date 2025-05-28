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

# Ad-hoc commands
Ansible ad-hoc commands used for system administration and automation. These are one-liners executed directly from the command line — useful for quick tasks, troubleshooting, or testing.

## 📦 APT: ansible.builtin.apt — Debian/Ubuntu Package Manager Module
⚠️ Needs to be run as root user (--become or -b flag)

    ansible test -m ansible.builtin.apt -a "name=apache2 state=latest" -b

## 🖥️ SHELL: ansible.builtin.shell — Run Shell Commands
Runs arbitrary shell commands on remote machines.

     ansible test -m shell -a "df -h"
     ansible test -m shell -a "uptime"
     ansible test -m shell -a "ps aux | grep apache2"
     ansible test -m shell -a "mkdir -p /opt/logs && echo 'shell command' > /opt/logs/Ad-hoc.txt"

📊 Shows disk space usage on hosts in test group.

## Use shell for:

  * Any command involving pipes (|), redirection (>), conditionals (&&, ||)

  * Environment variable usage ($PATH, $HOME)

  * Chained commands


## 📂 COMMAND: ansible.builtin.command — Run System Commands (No Shell Features)
 
          ansible test -m command -a "ls -lrt /tmp"
          ansible test -m command -a "ls -l /tmp"



## 📁 FILE: ansible.builtin.file — File Properties
Used to manage permissions, ownership, presence of files/directories.

            ansible test -m file -a "dest=/temp/exp.txt mode=0777 owner=ubuntu"
            ansible test -m file -a "path=/tmp/testfile.txt state=touch mode=0644 owner=ubuntu"
            ansible test -m file -a "path=/tmp/testfile.txt state=absent"



🎯 Ensures /temp/exp.txt exists, is owned by ubuntu, and has 777 permissions.

## 🔧 SERVICE: service — Manage System Services
Used to start, stop, restart, or enable/disable services like apache2, nginx, etc.

          ansible test -m service -a "name=nginx state=reloaded" -b
          ansible test -m service - a "name=nginx state= started"
          ansible test -m service -a " name=nginx state=started"






