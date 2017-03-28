# Ansible

## Articles

[Multistage Environments With Ansible](http://rosstuck.com/multistage-environments-with-ansible/)<br/>
[Using Host and Group Vars Files in Ansible](http://toja.io/using-host-and-group-vars-files-in-ansible/)


## Installation

OS X

```bash
brew install ansible
```

RHel

```bash
sudo yum install ansible
```

Ubuntu

```bash
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

Zabbix API

```bash
pip show pyzabbix
pip show zabbix-api
```

## Usage

Run playbook locally

```bash
ansible-playbook playbook.yml -c local
```

Create new role

```bash
cd path/to/roles
ansible-galaxy init rolename
```

Install roles

```bash
ansible-galaxy install rolename # by name
ansible-galaxy install -r requirements # from file
```

List Installed Roles in `roles_path`

```bash
ansible-galaxy list
```

Remove role

```bash
ansible-galaxy remove username.rolename
```

## Configuration

Ansible looks for configuration file as follows

```bash
./ansible.cfg
~/.ansible.cfg
/etc/ansible/ansible.cfg
```

Make sure to add your changes to the appropriate config file.

You can disable creation of retry file in ansible by modifying ansible configuration file.

```ini
[defaults]
# ...
retry_files_enabled = False
```

Specify hostfile

```ini
[defaults]
# ...
hostfile = hosts
```

Change roles path. You can specify multiple directories

```bash
roles_path = requirements:vendor
```