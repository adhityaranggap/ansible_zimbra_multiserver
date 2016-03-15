#  Module to install Zimbra multiserver from Ansible

Requirements
------------

* CentOS/RHEL 6, 7
* Correctly configure fqdn on virtual machine
* You have download Zimbra tgz and copy into `role/base/files`


Roles description
-----------------

1. `base`: Install the minimal packages, disable service, copy zimbra tgz, etc.
2. `zimbra-dns`: Install and configure the DNS service with information from global var (domain default, ip servers).
3.  `zimbra-ldap`: Install and configure the Zimbra Ldap server
3.  `zimbra-mailbox`: Install and configure the Zimbra Mailbox server
3.  `zimbra-mta`: Install and configure the Zimbra MTA server

Variables
---------

Configure global variables into  `grop_vars/main.yml` file
* `default_domain`: Default domain
* `zimbra_mailbox_fqdn`: FQDN to mailbox server
* `zimbra_ldap_fqdn`: FQDN to ldap server
* `zimbra_mta_fqdn`: FQDN to mta server
* `zimbra_password`: Password to ldap users (amavis, ladp replica, nginx, etc) . For more information you can see the `roles/zimbra-ldap/templates/ldap.j2`.
* `zimbra_tgz_name`: Zimbra tgz name
* `zimbra_folder_name`: Zimbra folder uncompressed
* `zimbra_path`: Zimbra path
* `zimbra_ldap_ip`: Ldap server ip
* `zimbra_mailbox_ip`: Mailbox server ip
* `zimbra_mta_ip`:  Mta server ip

The private variables into:
* From Zimbra Ldap:  `roles/zimbra-ldap/vars/main.yml`
* From Zimbra Mailbox:  `roles/zimbra-mailbox/vars/main.yml`
* From Zimbra MTA:  `roles/zimbra-mta/vars/main.yml`

Instalation
-----------
Role instalation  is:

1. Zimbra DNS
1. Zimbra Ldap
2. Zimbra Mailbox
3. Zimbra MTA

Execute Playbook
----------------
1. Install Zimbra Ldap Role
```yml
ansible-playbook -i hosts playbooks/zimbra-ldap.yml
```

2. Install Zimbra Mailbox Role
```yml
ansible-playbook -i hosts playbooks/zimbra-mailbox.yml
```

3. Install Zimbra MTA Role
```yml
ansible-playbook -i hosts playbooks/zimbra-mta.yml
```
