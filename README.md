# ansible-centos7_redmine
Ansible playbook to create redmine, unicorn and nginx on CentOS 7.

## Usage
### target hostname

* should be resolved to an IP address. (e.g. /etc/hosts)
* modify hostname in hosts file(inventorys)

### Linux admin account

admin account is used to connect via ssh.
This account is better the same as Ansible execution account.

* determine account name and password
* create hash from password
* modify account variables in group_vars/redmine-servers file.
* create ssh key pair if not exist.

### Linux redmine account

redmine account is used to setup, modify redmine, and execute unicorn.

* determine account name and password
* create hash from password
* modify account variables in group_vars/redmine-servers file.

### MariaDB root and redmine password

* determine root password and redmine password
* modify password variables in group_vars/redmine-servers file.

### Prepare ruby rpm file

This playbook, copy rpm file from ansible host to target, then install.

* put ruby rpm file in roles/ruby/files/
* modify rpm file variables in group_vars/redmine-servers file.

### Prepare redmine file

* put redmine tar archives in roles/redmine/files/

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

