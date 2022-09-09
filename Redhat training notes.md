Automation
- imperactive syntax/language
  scripting
- declaractive syntax/lang
  ansible / terraform / chef 
  
CI/CD


vi script1.sh
#!/bin/bash
# mkdir /dirA /dirB
touch /dirA/fileA
touch /dirB/fileB
if [[ condition1 -o condition2 ]] then
else
fi

chmod +x script1.sh
./script1.sh


individual shell
- functions / built-in shell binaries

ksh scripting
  if
  print
bash
  if
sh
csh
tcsh
zsh
perl
python

vi ls
cp /etc/passwd /etc/shadow /tmp
...
...
/usr/bin/ls

" " messages
' ' treat everything literallly
` ` backtick . to execute within 
messages
\ treat subsequent letter literally

$(cmd)


>
2>
<

cmd 1> result.log 2>&1





for
- short list
while
- long / unlimited / forever
- condition is still true
until
- condition is still false

if condition1/test
then
   true statement
elif condition2
   true
elif condition3
   true
else
   false statement
fi

if condition1
then 
   if condition2
elif
else
fi

" "
michael_jackson


crontab
- skip scheduled tasks
- 12pm backup files...
- what actually happens:
  11:50am, system rebooted 
  12:10pm
vs
anacron


man systemd.timer



docker - service / package

podman - kernel / package

ephemeral
- short-lived
- temporary
- non-persistent storage

persistent volume


Microsoft
- closed
- support
- license
Oracle

Container - standalone
- manual upgrade / update / healing / scaling
K8s - container orchestration
- auto upgrade / update / healing / scaling

K8s --> OpenShift

K8s v1.2.x Windows HOST
- only can run LINUX containers

Linux HOST
- Linux / Windows containers

podman pull

podman run


podman rmi 
= podman image rm


Rootfull container
- if hacker able to hack into that container, host OS security can be compromised
- not recommended

Rootless container
- more secured
- lot of restriction
- volume, network, 
- port forwarding > 1024

quay.io > docker.io

Create Containerfile
podman build
podman push 

webserver:test
webserver:staging
webserver:php-rhel
webserver:java-centos



K8s
- cluster --> node-pool (hw setup)--> nodes / VM --> POD --> Container

POD - single / multi container

web1, web2
- /videos
DB
email

K8s
- replicaset / recpliation controller


podman run
= podman create + podman start


Task: Start a WEb server using following details:
- mysql:version
- endpoint: https://url.com/web
- User supposed the query/access

Openshift
create template
- ...were supposed to be used by dept.
70%

namespace
cgroup

Stop container: podman stop

remove container: podman rm

remove image: podman -f rmi

remove all images: podman -af

Persistent Volume 
100 GB 

Persistent Volume Bind
container1 --> 1GB of PV
container2 --> 5GB of PV

Port Forwarding
Firewall
Persistent Storage + SELinux
- semanage fcontext -at container_file_t 
  '/home/user/db_data(/.*)?'
  restorecon -Rv
DNS

Netavark - new SDN
- ipv6, performance

Aardvark : DNS

HOST shutdown --> reboot
- Rootless Container --> shutdown 
- systemctl enable --> Reboot 
  must ssh user@host
  su / local login
- podman generate
- loginctl enable-linger
  systemctl --user enable 

Webserver1
- http24 image
- pv : /app-artifacts
- port forwarding 8080
- start and stop systemctl

useradd --system










