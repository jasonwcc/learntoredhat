cmd subcommand -paramter(s) argument
ls
cd
netstat
nmcli <tab>
man nmcli


click console on workstation
student / student
root / redhat


1. lab finish <script>
   lab start <script>
2. on rol lab interface
   - reset / shutdown / start
   - stop all VMs/ re-start all vMs
3. Delete / re-create the whole lab

unix/linux
- vi

- vim

i I
o O
a A
x
dd
dw
cw

yy
2y 
p P

:w!
:q
:wq!
:q!
ZZ
:100,105 move
:20,40 copy
:1,4 delete
:s
{
}
u undo last action
U undo all action on that line
:e! -- undo all changes
.  redo / repeat last action

/text
?text
n N


global substitution

:%s/old-text/new-text
:%s/old-text/new-text/g

YAML

set ts=2 sts expandtab
set list
set number
set nonu

rsh/ telnet (clear)


ssh
- disable password-based authentication
- enable key-based
  --> password-less

username / password
ssh 
- private (passphrase)

root

your account (username)
- remote db server (admin)


rsa
dsa
ecdsa

IBM Control / Insights

Netapp Insights
- netapp
- cisco
- ibm




RabbitMQ
- messaging platform



disk-based
network-based (NFS / CIFS)
pseudo (memory-based

Redhat
- during installation
 PCI-DSS 
\

UEFI
df -k
/
/var
/home

EFI

/boot GRUB


characters/raw/sectors
- 512b / unit

block
- 4k / unit

/var/www/html

partition --> mkfs (ext2-4,xfs).

soft/symbolic link
- shortcut link / pointer
- point using file path
- original file and the link can be in same/different file system
- ln -s <absolute-oath to target> link-name
- target can be file/directory
vs
hard link
- backup link
- point using inode
- original file and the link must be in 
same file system
- ln <absolute-oath to target> link-name
- only file


{}
[]
*
~

`` ~
''

Redhat cloud (private)
- insights
- openshift
- ansible (AAP)

rpm
- local package management
- display/check/verify
yum
- configure repository
dnf 
- configure repository
- better/improvised caching


Air gap


kernel-5.14
-- /boot/
kernel-5.15
-- /boot/

redhat v6
# yum group info
# yum group list


redhatv7

# yum group info
# yum groupinfo
# yum group list
# yum grouplist


BaseOSv1 --> v2
kernel
vi
binaries

Developmentv1 X-->v2
java
python

CentOS -> alma / rocky
remove baseos
keep appstream

ini
[section]


wget http://lab.domain19.example.com/redhat/aaa.gpg

1.8" 2.5" 3.5" 
HDD (spinder, platters)
- big capacity
- price lowest
SSD (flash-based)
- latency / speed
- 
NVMe-SSD

lsblk

block(4k) - fileA (5k)
block(4k) - fileB (1k)

fsck-level	ufsdump-level (backup)


CPU (6GHz) -- RAM DDR5 (5GHz)
NVME-SSD microsecond


RAID vs LVM
- 0 = mirroring
- 1 = concatenation
- 2,3,4
- 5 = stripe set with parity
- 6 = stripe set with double parity
- 10

spanned

linear LV

stratisFS
vdo

/data1

ext4
lvresize
resize2fs

xfs
lvresize
xfs_growfs



compression
- utilize idle cpu cycles
- big file 100m --algorithm-->20m
- compressive-friendly:
  database 80%-85% , virtualization 70-75%, oil & gas
- not compressive
  media (jpg, gif, mp4, mp3, mkv)
vs
deduplication
- utilize RAM to create the hashed table
- delete duplicate data / file

Netapp
 

Hard disk (1T) 
==> sales volume (500G) <-- 
==> hr volume (500g)
==> finance volume (500g)

Rootful Container
login as root
podman run --name web1 -p 80:80 -d httpd
- full access to networking (IP/dns/routing table/gateway)
- when the VM reboots, container restart
- systemctl enable/start/stop/disable

Rootless Container
login as non-root (rootless)
podman run --name web1 -p 8080:80 -d httpd
- limited
- when the VM reboots, container stop
ephmeral
- container ephemeral storage
- container can automatically if following:
  1. configure the container to start with   
     systemd
     - container start when user ssh / 
       graphical (login)
     podman generate systemd <container name>
     or
     podman generate systemd --new <container name>

  2. enable linger
     - when the VM reboots, container 
       restart
- systemctl --user enable/start/stop/disable


useradd -d -u -g ali
- rootless












nmcli con show
nmcli con add
nmcli con mod
nmcli con up


wget http:/<ul>/gpg...

configure repo
vi /etc/yum.repos.d/exam-objective-base.repo
[baseos]
name="description"
baseurl=http://....
enabled=1
gpgcheck=0
gpgkey=...

vi /etc/yum.repos.d/exam-objective-appstream.repo
[baseos]
name="description"
baseurl=http://....
enabled=1
gpgcheck=0
gpgkey=...

dnf repolist
dnf list
dnf install -y httpd mariadb mysql

firewall-cmd --permanent --add-service={http,mysql}
firewall-cmd --permanent --add-port=8080/tcp
firewall-cmd reload

semanage -l
semanage fcontext -at
semanage port -at 

systemctl enable --now httpd
systemctl enable --now mariadbd

rpm -q

useradd -g -G ali
usermod
userdel
groupadd
groupdel 
groupmod
passwd

su - ali
# crontab -e
* * * * * script/cmd

dnf -y install crond
systemctl enable crond  --now

mkdir

dnf -y install chrony
vi /etc/chronyd.conf
under pool line
server <hostname/ip>
systemctl enable chronyd --noew


dnf -y install autofs
vi /etc/auto.master
/rhome   auto.home
vi /etc/auto.home
ali   utility.servera.example.com:/rhome/ali
abu   utility.servera.example.com:/rhome/abu
#*     utility.servera.example.com:/rhome/&

systemctl enable autofs --now
ls -ld /dir/findfile
mkdir /dir/findfile
find / -user abu --exec cp {} /dir/findfile \;

grep
tar 

podman run --name test01 -v "/host-dir:/container-dir:Z"
podman generate systemd --new --file
mv test01.service ~/.config/container/systemd/user/
systemctl --user enable/top/start test01
loginctl enable-linger  

chmod

su - ali
vi .bashrc
umask 027


reset password

vgcreate
lvcreate -l 60 | -L 60M

vg PE=16M

mkfs
lvresize
xfs_growfs

parted
fdisk

mkswap

create normal parition
lsblk
vi /etc/fstab
UUID=
/dev/vgname/lvname	/mnt 	xfs defaults 0 0
UUID=<swap-uuid swap swap  defaults 0 0

systemctl daemon-reload


dnf -y install tuned
tuneadm recommend
==> balanced
tuneadm profile balanced
systemctl enable tuned --now



Exam voucher
- expiring

Quintegral

wired
- usb













