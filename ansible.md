# Ansible

## Installation

OS X

    brew install ansible

RHel

    sudo yum install ansible

Ubuntu

    sudo apt-get install software-properties-common
    sudo apt-add-repository ppa:ansible/ansible
    sudo apt-get update
    sudo apt-get install ansible

Zabbix API

    pip show pyzabbix
    pip show zabbix-api

## Usage

Run playbook locally

    ansible-playbook playbook.yml -c local

Create new role

    cd path/to/roles
    ansible-galaxy init rolename

Install roles

    ansible-galaxy install rolename # by name
    ansible-galaxy install -r requirements # from file

List Installed Roles in `roles_path`

    ansible-galaxy list
    
Remove role

    ansible-galaxy remove username.rolename

## Configuration

Ansible looks for configuration file as follows

    ./ansible.cfg
    ~/.ansible.cfg
    /etc/ansible/ansible.cfg

Make sure to add your changes to the appropriate config file.

You can disable creation of retry file in ansible by modifying ansible configuration file.

    [defaults]
    # ...
    retry_files_enabled = False

Specify hostfile

    [defaults]
    # ...
    hostfile = hosts

Change roles path. You can specify multiple directories

    roles_path = requirements:vendor

## Articles

[Multistage Environments With Ansible](http://rosstuck.com/multistage-environments-with-ansible/)<br/>
[Using Host and Group Vars Files in Ansible](http://toja.io/using-host-and-group-vars-files-in-ansible/)
