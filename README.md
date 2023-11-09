# Install docker on debian with ansible

### Ansible role to install Docker on an instance with Debian 11 or 12.


## Prerequisites

### Install Ansible

#### Use the package manager according to the operating system you have:

* Fedora
```
sudo dnf install -y ansible
```

* CentOS
```
sudo yum install -y ansible
```

* Ubuntu/Debian
```
sudo apt install -y ansible
```


### Install Python3

* Fedora
```
sudo dnf install python3
```

* CentOS
```
sudo yum install python3
```

* Ubuntu/Debian
```
sudo apt install python3
```


## Before executing ansible role

* Change the name of the file [test_ec2.yml](/ansible/docker/inventory/group_vars/test_ec2.yml) by the name of your instance.

* Change the value of the private key in [ansible_private_key_file](/ansible/docker/inventory/group_vars/test_ec2.yml#L1).

* If necessary, change the value of the username in [ansible_ssh_user](/ansible/docker/inventory/group_vars/test_ec2.yml#L2).

* Change the value of the profile name in [aws_profile](/ansible/docker/inventory/aws_ec2.yml#L2).

* If necessary, change the value of [regions](/ansible/docker/inventory/aws_ec2.yml#L4).

* Change the value of [groups](/ansible/docker/inventory/aws_ec2.yml#L10). Must be the same as the filename in [group_vars](/ansible/docker/inventory/group_vars/test_ec2.yml).

#### If you want execute ansible role on debian 11 or debian 12, just comment out the role you don't want to execute in [main.yml](/ansible/docker/main.yml).


## Run ansible playbook

```
ansible-playbook -i ansible/docker/inventory/aws_ec2.yml ansible/docker/main.yml
```


## Usefull commands

#### Check if the inventory works correctly:

```
ansible-inventory -i ansible/docker/inventory/aws_ec2.yml --graph
```

```
ansible-inventory -i ansible/docker/inventory/aws_ec2.yml --list
```