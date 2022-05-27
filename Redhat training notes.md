```
chmod (RH124)
- octal
- symbolic

umask (RH124)
- by default permission:  
  file (666) /dir (777)
- effective permission for newly created file (644) /directory (755)
- apply user-owner,group-owner,other permissions only

chgrp (RH124)
chown (RH124)

setuid (RH124)
- set user id:
- set on executable file
executable file (ownership) - user1
user who execute the process - user2
process (ownership) - user1
- top / ps

setgid (RH124)
- 1. set group id
- set on executable file
- 2. inheritancy (ownership)
  parent dir: group1
  - new file : group1

sticky bit (RH124)
- set on public dir with full permission granted to everyone
- only owner able to delete their owner

setfacl
- configure additional user/group
- ACL mask: max permission

default:g:group1:rwx #rwx
default:g:group2:r-x #r-x
default:g:group3:r-x #r-x
default:g:group4:rw- #rw-
default:g:group5:rw- #rw-
default:mask::rw-

journald (RH124)
--> journalctl 
--> /run/log
    ACL
--> volatile (after reboot)

syslog 
- text / universal / old
- persistent (10yrs)
- /var/log

Managed Devices - removable
- cdrom / cdrw / dvdrom / optical
- Tape (LTO3 : LTFS)
- usb / flash / thumbdrive

setfacl -mR u:jason:rwx /testA
- everything will set to jason:rwx
setfacl -mR u:jason:rwX /testA
- apply only on dir not regular file
-R recursive
file jason:rw
subdir# jason:rwx

Set acl using stdin
getfacl file1 | setfacl -M - --set-file=file2

Copying/Restoring ACL
- 1. getfacl > file1
- 2. setfacl --set-file=file2

Delete all ACL
# setfacl -b dir/file

Set default ACL for newly created file/dir
# setfacl -m d:u:jason:rw- file/dir
or
# setfacl -m -d u:jason:rw- file/dir

Delete default ACL for newly created file/dir
# setfacl -x d:u:jason:rw- file/dir
or
# setfacl -x -d u:jason:rw- file/dir


getboolean
- current state:on/off

semanage boolean -l
- current/boot state: on/off


Type of Disk (2.5" / 3.5")
- SSD (flash - 1.8")
  - SAS (24GB/s)
  - NVMe
- HDD /dev/hdX
  - SAS
    - 10k/15k rpm
  - NL-SAS
    - 5400 rpm - 7200 rpm
  - IDE 

SCSI
- /dev/sdX
NVMe
- /dev/nvmeX

Storage Array
- NAS
  - Ethernet / IP 
  - CIFS / NFS
- SAN
  - FC / FCoE
  - iSCSI 
  - NVMeoFC
- DAS

access method by OS 
- c : characters / sectors (512b)
- b : block (4k/8k)

Pseudo-based FS / Memory-based
- accessed / managed by the kernel

dump indicator    fsck-priority
x                 y

REDHAT
- 1st --> 
- 2nd --> /dev/sdb
- 3rd --> /dev/sdc
- 4th --> /dev/sdd


PE size 4m
What if i create a 100m LV?
- 25 PE. Perfect
What if i create a 110m LV?
- 28 PE. LVM create 112m LV

Standard LV (standalone
Concatenated (RAID-0)
- different number of PE on different PV
- flexible of expanding
- not protected

Stripe set without parity (RAID-0)
- has best performance
- cannot expand
- not protected

Block Size 
- configured on FS / mountpoint
  mkfs 4kb / 8kb / 128k
  - how large this FS can be created?
  - smallest LV can be created?


vs PE size
- configured on VG 
  vgcreate 4m / 8m / 16m / 128m
  - how large this VG can be created?
  - smallest LV can be created?

RAID-10 
- sw-based
- hw-based (configured array controller)

pvcreate
pvs
pvdisplay
- PEs

vgcreate
vgs
vgdisplay

lvcreate
- specify actual capacity / specify number of PE

lvs
lvdisplay

pvmove
- move PE from one PV to another PV

- cannot move PV from one VG to 
another VG

/boot
--> cannot be placed on LVM
--> GRUB loader
/
/usr
/etc

Mapper
FS --> LV --> PE --> PV

Storage Efficiency
1TB -- USD100
- Compression
  - Use CPU alot
  - LZ4 algorithm (4kb)
  - focus speed rather compression ratio
  - about 500Mb/s per core
  - app/data compressible friendly
    - DB (80-85%), 
    - Virtual-related(70-75%, 
    - oil & gas (60%)
    - user data)
       dont use compression here
       - office 2016 xlsx,pptx,docx)
       - video / audio mp3 mp4 mkv avi

- Deduplication
  - Use RAM alot
  - remove redundant content
    - 4kb


Dracut
- create initramfs

Initramfs
- consists important executable binaries/libraries
- RAM (performance)

Root FS = /
/usr/lib
/usr/bin
/usr/sbin

/etc
 
/var
/tmp
/home
/root
/boot


runlevel --> milestone --> target

Imperative language
- scripting
  - step 1 --> 2 --> 3
vs
Declaractive
- declare the desired state
```
1st-column 
dump-level 
- backup / old
- lower number first 

2nd-column
fsck-check-level
backup

BaseOS-Stream
- OS v8.1 --> v8.2
- 

AppStream
- RunTime environment
- Java v1.0 
- Mysql v1.0 


KickStart
- automated installation network
- dhcp / pxe-compliant NIC
Solaris Jumpstart
AIX NIS
Windows SCOM
- sysprep 

Monolithic design
- image
  - db, email, ftp, www, python
  - better performance (latency)
  - better contract security 
vs
Micro-service
- image1 -> function / process
  - adaptability 
  - scalability
- processes hosted on different node
  - network latency risk
  - security risk

Container Image registry
- quay.io
- docker.io
- Google CR
- Azure CR
- redhat.io
  
Container processes
- are built to be ephmeral (temp / short-lived)
--> CI/CD Continous Integration / Continous Delivery / Deployment


Base Image
---> child images


Community Developer
--> Virus / Hack / 
    bugs / unknown packages

Run podman 
- using root account
  : all privileges
  
- using non-root account / root-less 
  : limited privileges 
    --> network limited 
    --> storage 

podman inspect 
--> locally downloaded image
skopeo inspect
--> local / remote (docker://)

podman run --name web1 -d docker.io/library/httpd
-d detached / background 
- download image if not available locally
- /etc/containers/registries.conf
  -- sequence
podman run ubuntu

user1 --> host (8080) -- port forward --> myweb1 (80)
user2 --> host (8181) -- port forward --> myweb2  (80)

- Naming resolution services
-> /etc/hosts / DNS (2) / NIS  / NIS+ / LDAP (3)
- ping servera / tracert /browse 

/etc/hosts (1)
- mapping IP to host
192.168.0.100 servera
192.168.0.101 serverb.example.com

/etc/nsswitch.conf 
--> determine the sequence
    1 > 2 > 3

DNS 
- resolved FQDN into IP 

/etc/resolv.conf
-> where DNS server IP / hostname
nameserver 192.168.0.201
nameserver 8.8.4.4
domain example.com
search example.com jason.com trainocate.com


container
- ephemeral
- container storage 

ansible / orchestration / declaractive
- idempotent


podman rmi
- remove image
podman stop 
podman rm
- remove stopped processes


podman run -p x:y
x what ur current host will listen to
y what the container are configured to listen to
  find out from docker / redhat document
  httpd - 80
  mysql - 3306

- if rootless, CANNOT run and forward using x=80

podman stop --> podman rm
or
podman rm -f 

podman rmi -f
--> podman rm -f --> podman rmi 

mkdir /dir
chown ; chmod / setfacl
semanage fcontext -at container_file_t "/dir(/.*?)"
restorecon -Rv /dir

podman -v "/dir:/var/lib/mysql:Z" mysql


shutdown host --> boot up host
--> shutdown all containers --> boot ??
    --> podman start 
    --> do not podman run 

systemctl 
- if user execute will get error
  then linger

Ansible 
- open source
- acquired RH
- modules built based python
- agentless orchestration utility / framework
  - install/patch OS (windows / Linux)
  - configuration (partition / formatting / package)
  - network devices (cisco switch/router)
         ssh 
- master node
  --> ansible package
  --> python runtime
  --> passwordless ssh login
- playbook - idempotent tasks
   go into servera,serverb,serverZ 
   --> create user ALI --> install httpd
   --> systemctl start/enable httpd --> configure FW
   --> selinux
ansible-playbook
ansible-...

Ansible tower
- Web UI
- RBAC / security / project 
- license 
RH254
vs
- script
  --> if check user ALI already
  --> parallel over CPU
  















