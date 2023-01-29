# Linux 
1. Change all user passwords. Yes, especially the credentials given to you!
```
passwd username
```
2. Audit /etc/shadow for users with passwords set, or no password at all.
```
cat /etc/shadow
```
3. Remove all SSH keys present on the box.
```
find / -name authorized_keys 2> /dev/null
```
```
find / -name id_rsa 2> /dev/null
```
4. Audit sudo access given to users.
```
cat /etc/sudoers
```
```
cat /etc/sudoers.d/*
```
```
getent group sudo | cut -d: -f4 (The sudo group is Debian, wheel is for RHEL)
```
5. Audit /etc/passwd to check for account shells and UIDs.
```
cat /etc/passwd | grep :0:
```
```
cat /etc/passwd | grep -v /bin/false | grep -v /sbin/nologin
```
6. Verify that there are not any non-standard cron jobs on the system.
```
cat /etc/cron.d/*
```
```
for user in $(cut -f1 -d: /etc/passwd); do crontab -u $user -l; done
```
7. Remove packages that could be used for malicious purposes if not needed.
```
apt remove socat nc ncat nmap netcat (apt is for Debian, yum is for RHEL). Other packages must be manually inspected in order to prevent taking down critical services.
```
8. Stop services that are not critical to the system or competition needs.
```
systemctl --type=service --state=active
```
```
systemctl stop servicename
```
9. Identify SUID and SGID files. Cross-reference with https://gtfobins.github.io/ to narrow down malicous instances of SUID and SGID files.
```
find / -perm -4000 -print 2>/dev/null for SUID
```
````
find / -perm -2000 -print 2>/dev/null for SGID
````
10. Identify world-writable files and directories.
```
find / -type d \( -perm -g+w -or -perm -o+w \) -exec ls -adl {} \; for directories
```
```
find / ! -path "*/proc/*" -perm -2 -type f -print 2>/dev/null for files
```
11. Check who is currently logged into the machine.
```
$ who
```
