RH134 Nov 2025
" " - display message, $^~? 
' ' - display everything literally
` ` - backtick. command substitution . Similar to $(cmd)

PS1 = prompt setting level 1
PS2 = prompt setting level 2
PS3 = select statement
PS4 = debug

Initialization file
/etc/profile  call /etc/bashrc

/etc/bashrc
var1=100
var2=200
var3=300

~/.bash_profile --> /bashrc
var1=111
var4=400

~/.bashrc
var1=1111
var5=500

variable="data"
alias="commands"

if a=100 and b=200
[ ]
[[ ]]
( )

case

for i in a b c d
do
 cmd1
 cmd2
done

while [while condition is still true ]
do
 cmd1
 cmd2
done

until  [while condition is still false]
do
 cmd1
 cmd2
done


noglob off ==> glob (enable * to be used as wildcard)
noglob on  ==> no glob (disable * as wildard)


at - run job(s) at specific date&time
batch - run job(s) when system average load / busy
cronjob - run job(s) repetitively
anacron - run job(s) repetitively - reboot/hibernate
systemd timer

everyday 12pm backup; transfer to nfs server; package update
mon 12pm
tue 11:55pm down/crash
tue 12:05
wed

root / redhat
student / student

system log 
- rsyslog 
  -- text based 
     -- grep/less/more/sed
  -- persists
  -- /var/

- systemd-journald
  -- binary/indexed 
     -- complex/advanced query
     -- better performance
  -- does not persists
  -- /run/


ali su root
vi /etc/profile
vi /etc/profile.d/profile1.sh
vi /etc/rsyslog.d/ali.conf


mary su root
vi /etc/profile
vi /etc/profile.d/profile2.sh
vi /etc/rsyslog.d/mary.conf


/var/log/firewalld
/var/log/firewalld.20251111 

tar -cJvf 

ftp
- send data over network in plaintext format

vsftpd

ftps
- based on TLS/SSL
sftp
- utility provided by the openssh suite
scp -r /dirA remote:/tmp/


rsync
- copy only delta / changed files

INTEL/AMD
- hyperthread
- core 

ARM/IBM Power/Sparc
10 core x 1/2/4/8 = 80 threads

CPU -  socket
1 x 20cores x 1/2 threads = 80 threads
4x2cores

Databases
apache
java-based

GPU
LLM
Gaming
AI/ML

TensorFlow PU

c - character/sector : 512b/s
b - block : 8k/b

RAM 1000 Mb
OS   200 Mb
PPT  100 Mb (50% data pages inactive)
XLS  200 Mb (50% inactive)
Word 300 Mb

CPU vs Memory - GHz/1000 MT=10GT
NVMe single digit microsecond

SAP HANA
REDIS 
vs
Oracle
vs 
MS SQL


Create an LV named abc01 with a physical extend size of 16m. Make sure the abc01 has 60 physical extent. Mount the lv using xfs to /mnt/database persistently.
vgs
lsblk # look for available / unused disk(s)
vgcreate -s 16 datavg /dev/sdc
lvcreate -l 60 -n abc01 datavg
mkfs.xfs /dev/datavg/abc01
mkdir /mnt/database
vi /etc/fstab
/dev/datavg/abc01 /mnt/database xfs defaults 0 0
mount /dev/datavg/abc01 /mnt/database


vgs
vgdisplay
lvs
lvdisplay
pvs
pvdisplay

Increase FS size
lvextend
xfs_growfs

1. fdisk
2. mkfs = format
3. mount / map to drive


3:30pm

AUTOFS
user
# cd /mnt/database
autofs will automatically execute mount -t nfs 192.168.5.100:/database /mnt/database
# cd /
autofs will automatically unmount /mnt/database

root can execute mount

server
/database o=rwx

user --> nfs --> nobody
cd /mnt/database






























