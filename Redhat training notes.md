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

Round Robin
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
- control effective permission of newly created file/directory

newly created files - 666 (rw-rw-rw-)
newly created dir   - 777 (rwxrwxrwx)
effective file	    - 644 (rw-r--r--)
effective dir	    - 755 (rwxr-xr-x)

Acl
- mask = max permissions








