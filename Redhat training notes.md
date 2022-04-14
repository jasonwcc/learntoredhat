chmod +x script.sh

1
cd ~
./script.sh

2
/home/student/script.sh

3
cd
sh script.sh


scheduling
Process 1 - 500ms (timeslicing)
Process 2 - 450ms
Process 3

DNS
LACP
NIC TEAMING
TimeSharing (TS)
RT
-99


File & directory permissions (rwx)
ls -l
file owner 	- permission
group owner
other (public)


RH124
Special permission
- sticky bit - owner can delete his/her
- setuid - executable binary
- setgid - set group ownership on subdir

process owner
umask 0023
- control effective permission of
newly created file/directory

newly created files - 666 (rw-rw-rw-)
newly created dir   - 777 (rwxrwxrwx)
effective file	    - 644 (rw-r--r--)
effective dir	    - 755 (rwxr-xr-x)

Acl
- mask = allowable max permissions
- named user - acl
- named group - acl
- group owner - acl
- "default acl" - permission apply to parent dir
  - inherit default acl permissions new files/sub-directory

getfacl
setfacl

chmod
- user execute

chgrp
- user execute

chown
- user cannot execute

base
owner: jason : rwx
group: sales : rx
other: ---

Acl
user: peter :
group: engineer :
mask:

Precedence
- final result / effective permission

setfacl -R -m u:peter:rx /dira/*

- conditional execute permissions
```
file -
dir x
```

- Network Services :
```
NTP
DNS
DHCP
SMTP
```

- LDAP
```
centralize user/group
policies
profiles
rbac
hostname
```

- MS DS (AD)
based on LDAP



- Configure web server / db server /  NFS-server / autofs
```
1. install packages
# dnf -y install httpd
# rpm -ql httpd | grep ".*service"
2. Start and Enable the Services
# systemctl start httpd
# systemctl enable httpd
3. Enable the service on firewall
# firewalld-cmd --permanent  --add-service=http
4. [optional] Enable SELinux
# semanage fcontext -at httpd_sys_content_t \
"/var/www/html(/.*)?"
# semanage port -at http_port_t -p tcp 8800
```
task
1 - 0
...
10

10-20

performance-based
210/300

IaC
puppet chef ansible terraform
- orchestration framework
- yaml,json,jinja2

ansible-playbook aa.yaml
- master node / Configure
- managed nodes
  - python


general workloads
- DB (Oracle / Mongo / Microsoft)
- WEB (cgi, wscgi,...)
- EMail
- Messaging
- SIEM / SOAR
VM
- SAP HANA

VM
- linux (cgroup, scheduler )
containers = process
- containerized workloads
- DB (Mongo, mysql , oracle)
- purpose built
- redis in-memory
- shared ,
- cgroup
-

Containerfile Dockerfile
- DO180


podman rm WEB
podman rmi web-image

mkdir /home/user/dbfiles
semanage fcontext -at "container_file_t" "/home/user/dbfiles(/.*)?"
restoreconv -Rv /home/user/dbfiles/
