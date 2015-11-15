# ansible-centos7_redmine
Ansible playbook to create redmine, unicorn and nginx on CentOS 7.

## Usage
### target hostname

* should be resolved to an IP address. (e.g. /etc/hosts)
* modify this playbook's inventry file(hosts)

### Linux admin account

admin account is used to connect via ssh.
This account is better the same as Ansible execution account.

* determine account name and password
* create hash from password
* modify this playbook's group vars file(redmine-servers)
* create ssh key pair if not exist.

### Linux redmine account

redmine account is used to setup, modify redmine, and execute unicorn.

* determine account name and password
* create hash from password
* modify this playbook's group vars file(redmine-servers)

### Execute

There are 2 steps to execute ansible-playbook.

+ use root to ssh connect

```
ansible-centos7_redmine$ ansible-playbook -i hosts -u root -k site.yml
```

+ use admin account to ssh connect

```
ansible-centos7_redmine$ ansible-playbook -i hosts site.yml
```

