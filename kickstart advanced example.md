```
# Common setups
keyboard us
lang en_US.UTF-8
timezone --ntpservers=asia.pool.ntp.org Asia/Kuala_Lumpur
selinux --enforcing
url --url="http://classroom.example.com/content/rhel8.2/x86_64/dvd/"
repo --name="appstream" --baseurl=http://classroom.example.com/content/rhel8.2/x86_64/dvd/AppStream/

# Configure bootloader configuration
bootloader --append="rhgb quiet crashkernel=auto" --location=mbr --boot-drive=sda

# System authorization , possilbe (NIS,NISplus,LDAP)
auth --useshadow --passalgo=sha512
# Install using text mode, by default GUI
text
skipx
clearpart --drives=hda,hdc,sdb,sdc
zerombr
# Configure MBR partitions from each disk (GB)
part raid.11 --size 1000 --asprimary --ondrive=hda
part raid.12 --size 1000 --asprimary --ondrive=hda
part raid.13 --size 2000 --asprimary --ondrive=hda
part raid.14 --size 8000 --ondrive=hda
part raid.15 --size 16384 --grow --ondrive=hda
# --grow option to let fill all remaining available space
part raid.21 --size 1000 --asprimary --ondrive=hdc
part raid.22 --size 1000 --asprimary --ondrive=hdc
part raid.23 --size 2000 --asprimary --ondrive=hdc
part raid.24 --size 8000 --ondrive=hdc
part raid.25 --size 16384 --grow --ondrive=hdc

# Configure the MD RAIDs
raid / --fstype xfs --device root --level=RAID1 raid.11 raid.21
raid /safe --fstype xfs --device safe --level=RAID1 raid.12 raid.22
raid swap --fstype swap --device swap --level=RAID1 raid.13 raid.23
raid /usr --fstype xfs --device usr --level=RAID1 raid.14 raid.24
raid pv.01 --fstype xfs --device pv.01 --level=RAID1 raid.15 raid.25

# LVM configuration so that we can resize /var and /usr/local later
volgroup sysvg pv.01
logvol /var --vgname=sysvg --size=8000 --name=var
logvol /var/freespace --vgname=sysvg --size=8000 --name=freespacetouse
logvol /usr/local --vgname=sysvg --size=1 --grow --name=usrlocal

# Configure non-RAID or non-LVM
part /databases --fstype="xfs" --ondisk=sdb --size=10000
# part / --fstype="xfs" --ondisk=hda --size=10000


# Start service on nxt boot
services --enabled=httpd,mariadb,firewalld,chronyd --disabled=network,iptables,ip6tables

# Configure networking
network --device=eth0 --bootproto=dhcp
network --device=eth1 --bootproto=static --ip=192.168.32.101 --netmask 255.255.255.0 --gateway=192.168.32.2 --nameserver 8.8.4.4,8.8.8.8
network --hostname=r9s1.example.com
firewall --enabled --http --ftp --smtp --ssh --port=8080,8181

# Configure Root and user password
rootpw --iscrypted --password=<echo "password | sha512">
group --name=accounts --gid=10001
user --name=student --password=<echo "password | sha512"> -iscrypted --gecos="Its non-root account"
user --name=jdoe --password=cangetin --plaintext --gecos="John Doe the accountant" --groups=accounts


# Anaconda logs to syslog server during installation
logging --host=192.168.32.201 --level=info
#logging --host=loghost.example.com --level=info

# Enable initial setup (choose data & time, network configuration, user settings) the first time reboot
# For this to work, must install the initial-setup package. by default is off
firstboot --enable

%packages
@^graphical-server-environment
@debugging
@development
@security-tools
@java-platform
@virtualization-hypervisor
@virtualization-platform
@virtualization-tools
@virtualization-client
httpd
mariadb-server
mariadb-common
%end

%pre
%end

%post
mkdir -p /test-dir/accounting
setfacl -m u:jdoe:rwx /test-dir
setfacl -Rm g:accounts:rX /test-dir
%end

```
