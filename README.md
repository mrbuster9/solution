# solution

Created Two VMs provided on VirtualBox

First VM name in vagrant as web ip 192.168.2.31
Last VM name in vagrant as db ip 192.168.2.32

Root user MySQL:
Login: root
Password: 111

Simple user MySQL owner wordpress db:
Login: test
Password: 222

LDAP authentication configured for using Group ou=mathematicians,dc=example,dc=com
Test login passed on gauss:password

##Ansible roles in recreate.yml:
wordpress - install: CMS wordpress, extensions. Configuring apache2

mysql - install: mysql-server, extension. Create DB wordpress, create user test.

user - create user serviceuser with password 111 and access to execute only systemctl ower sudo

After execute clone repo and execute vagrant up, open in you browser http://192.168.2.31
