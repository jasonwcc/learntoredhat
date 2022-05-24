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



```
