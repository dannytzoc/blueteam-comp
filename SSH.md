## CentOS / RHEL / Fedora / Redhat / Alma / Rocky Linux Restart SSH

Type the following command on an older RHEL version:
```
/etc/init.d/sshd restart
```

One can use the service command:
```
service sshd restart
```

If you are using RHEL/CentOS/Fedora Linux with systemd (e.g. RHEL or CentOS v7/8/9+), enter:
```
sudo systemctl restart sshd
```
How to restart the SSH in Debian / Ubuntu Linux
Restarting ssh is simple job, exeute:
```
/etc/init.d/ssh restart
```

OR
````
service ssh restart
```

OR
````
sudo service ssh restart
```

If you are using Debian/Ubuntu/Mint Linux with systemd, use the systemctl command:
````
sudo systemctl restart ssh
````
https://www.cyberciti.biz/faq/howto-restart-ssh/ 
more link 

