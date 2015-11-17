# ansible-centos7_redmine
Ansible playbook to create redmine, unicorn and nginx on CentOS 7.

## Usage

### settings

#### hostname

* Modify hostname in 'hosts' file(inventorys).  
This name is set as target's hostname.
So, this name should be resolved to an IP address. (e.g. /etc/hosts)

#### Linux admin account

This admin account is used by ansible to connect via ssh.

* Default account is 'admin', and password is 'admin'.
* Default account'S Public key is ~admin/.ssh/id_rsa.pub
* To change, modify account variables(name and password) in group_vars/redmine-servers file.
  * Password should be described as hash string, not plain text.
  * Create ssh key pair (RSA) if not exist.  
This playbook use an 'id_rsa.pub' in the .ssh/ in the account's home.

##### Linux redmine account

redmine account is used to setup, modify redmine, and execute unicorn.

* Default account is 'redmine', and password is 'redmine'.
* To change, modify account variables(name and password) in group_vars/redmine-servers file.  
  * Password should be describe as hash string, not plain text.

#### MariaDB root and redmine password

MariaDB root account's password, redmine account's password.

* Modify password variables in group_vars/redmine-servers file.

#### put ruby rpm file

This playbook, copy rpm file from ansible host to target, then install.

* put ruby rpm file in roles/ruby/files/
* modify rpm file variables in group_vars/redmine-servers file.

#### Prepare redmine file

This playbook, copy tar ball file from ansible host to target, then install.

* put redmine tar archives in roles/redmine/files/

### Execute

There are 2 steps to execute ansible-playbook.
At first, use root to ssh connect. This needs to create linux admin account.

```
ansible-centos7_redmine$ ansible-playbook -i hosts -u root -k site.yml
```

Once created linux admin account, then can be used the account to ssh connect.

```
ansible-centos7_redmine$ ansible-playbook -i hosts site.yml
```


