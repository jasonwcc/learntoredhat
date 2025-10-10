Primary group
- user must have one
- used to own file/directory/process/print job
- assign permissions

Secondary/Supplementary group
- user can belong to none or upto 15 groups
- switch primary
- assign permissions

DEMO
- groupadd/groupmod/groupdel
- useradd -g user / userdel / usermod / passwd
- su - user
- chgrp : permanently change group ownership of file/directory
- newgrp: temporarily switch primary group 


- chown : change user ownership of file/directory
        : only root can execute

setfacl

login user

su 	# incompletely login as root
su -	# completely login as root
password root:

sudo shutdown 
password user:


root
student add to wheel


%wheel	ALL=(ALL:ALL)	ALL
%wheel	r10s1.example.com=(operator:groupname) 	command

user1	sudo	assumed as operator

%games ALL=(ALL) /bin/id
groupadd games
useradd -G games user4
login as user4
$ sudo /bin/id


groupadd
group







Delete user only : userdel username
Delete user and its home directory respectively : userdel -r username


usermod -aG
groupmod -aU

passwd jason
abc
passwd peter
abc

1-jan-1970
8-oct-2025

20xxx

usermod -e
chage -E

service/process/application directly




file - compulsory r
dir - comp. x

Permission is assign user/group to file/dir
SELinux is assign process to file/dir








maindir -rwxr-xr-x	--> rwxr-xr-w
  subdir rw-rw-rw-  	--> rwxrwxrwx
    fileA  rw-r--r--	--> rw-r---r--
    subsubdir rwxr-xr-x	--> rwxr-xr-x
      fileB rwxr-xr-x	--> rwxr-xr-x


chmod -R +X maindir/*

chmod 1644 file

r	w	x
4	2	1	
/	x	/	5
/	/	x	6
/	/	/	7
x	x	x	0
x	/	/	3


chmod 4644 = set user ID (suid) = chmod u+s
- assign to an executable binary file
- show process ownership of the person creates the binary\
- /public/pgmA

chmod 2644 = set group ID (sgid) = chmod g+s

chmod 1644 = set sticky bit  = chmod +t



Linux/unix kernel

			file 		dir
original-perm		(666)rw-rw-rw-	(777) rwxrwxrwx
umask 	substract	(033)----wx-wx	(033) ----wx-wx
=			 644 rw-r--r--   755  rwxr--r--





rpm
- manage packages/software locally

dnf
- manage packages/software from repository
- resolve dependencies

Repository


a.b.c.d
V R M F


rpm -ivh bash-5.2
does not 	--> install
installed (5.1) 		--> upgrade/update
- binary			--> binary/libra/doc/5.2	
- library
- doc
- configuration(change)
- kernel

yum

dnf


BaseOS-7.1			-> 7.2
- kernel 7.2
- FS
- vi
AppStream
- java-7.1
- python-7.1



b lock (4k/8k)	              : ls / touch / cd
c haracter/raw/sector (512b) : OS/Kernel access thru 


Mount manually
# mount

Mount automatically during boot time
# vi /etc/fstab

Mount on demand
# cd /mnt
# cd ..
learn in RH134

lsblk --fs
- copy code to the partition
mount UUID="paste UUID from above cmd" /database

ls
locate
- built index file (mlocate database)

find "location" "-criteria"
-name
-uid
-perm
-type
-mtime
-link
-inum
..
...


find / -perm /222
fileA 223
fileB 334
fileC 111
fileD 331

modify / create / access

-mmin -5
-cmin -5
-amin
-ctime
-atime
--mtime










 - C1 (102) 	--> zombie
   - GC (103)
 - C2 (104)

kill -15 101	: gracefully ask the whole process family

kill -9 104	: forcibly kill the whole process family


ps -aux
ps aux

Process control
- system wide
- ps -ef | top

Job control
- session based
- job

ctrl+c --> INT
ctrl+\ --> QUIT
cltr+z --> TSTP

kill -1 / kill -HUP / kill -SIGHUP






cpu 
- physical 10xprocessor (6.2 GHz)
- logical processor (thread)

If u are using Intel/AMD cpu
- 10xcore = 20 threads

If u are using IBM Power/Oracle Sparc cpu
- 10core = 80 threads

Thread benefiacial


initd
- systemd
- service start/stop


service - individual process/application
target - group of services / milestone

systemctl start sshd
systemctl enable sshd
= systemctl enable --now sshd

fexx - link-local, cant connect outside of subnet 169.254.x.x
fc/fd - unique-local, can't connect into internet
2xxx - global/public ip
ff   - multicast   224.x.x.x - 239.x.x.x
::1   - localhost 127.0.0.1
::    - unknown 0.0.0.0

0.0.0.0 - 255.255.255.255  
0.0.0.1 - 0.0.0.200






PC1 : 192.168.0.1 
      255.255.0.0
PC2 : 192.168.1.6 
      255.255.0.0
Are they in same subnet? Y/N



255.255.255.0  /24
8n.8n.8n.8c    = 24
255.255.0.0    /16
255.240.0.0    /14


1111 1111.1110 1000

128 1000 0000
192 1100 0000
224 1110 0000
240 1111
248 1111 1
252 1111 11
254 1111 111
255 1111 1111
0
1000 0000.0000 0000.0000 0000.000000

MAC




192.168.100.101/27

subnetmask : 255.255.255.224



decimal 10 100 1000  1104

binary
abcd
1011 

octal

hexadecimal
0-9,a-f
IEEE
00:0c:29:e9:5b:be
1st convert ipv6 into binary
0000 0000:0000 1100: 
2nd toggle bit number 7th
0000 0010:0000 1100: 
02:0c:29:e9:5b:be
3rd insert ff:fe in the middle
020c:29ff:fee9:5bbe
4th insert fe80::
fe80::20c:29ff:fee9:5bbe


ifconfig (deprecated)
ip address
ip link
netstat
nmcli - configure network permanently


nmcli con add ... . ....
nmcli con mod
nmcli con up


SSH
- use HOST keys (pub/pri)
- use USER password (default)
- use USER keys (pub/pri)

1. Must login using username/password
2. After generate, copy the public key to authorized_keys
  - can login without passwd
  - can login using user/passwd
3. why Passphrase? prompt in the event private key being used.
  enter passphrase
4. Login without password + passphrase
   start a terminal
   configure/start ssh agent
   add private-key + passphrase to the agent

/etc/ssh/sshd_config
PermitRootLogin prohibit-password : root must login using key
PermitRootLogin yes : root can ssh login using passwd/key
PermitRootLogin no  : root cannot ssh at all 

PasswordAuthentication: yes	: all user including root can login using passwd
PasswordAuthentication: no	: must login u

rh124
rh134
ex200 - 


training + exam
- ask salesperson/am
- DHL contact casey

exam voucher 
- 1 yr expiry











