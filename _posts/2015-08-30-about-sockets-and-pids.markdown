---
layout: post
title: About Sockets and Pids
date: 2015-08-30 21:47:02.000000000 +05:30
---

# Sockets
 
  Sockets are used to allow two way communication between processes either its internal or with two external systems. The communication is of either through TCP or UDP packets.

Sockets run at /var/run
But /var/run is a link to run so we can type /run

<code>
  ls -l /run
  # -l is long list and ls is used to list files.
</code>

swdd-rw-----1 root docker docker.sock

where s is socket which owned by root but accesssing  by group docker which had root privileges

### Adding users to group
check groups list
<code>
  cat /etc/group
</code>
add user to group

<code>
  sudo gpasswd -a username groupname
</code>

restart it to get changes to be affected


### Check all listeners on network ports
<code>
netstat -tlp # tcp listening program
</code>

### Bind docker to listen to network port instead of local unix socket
Network ports doesn't require permissions to access and communicate. 
<code>
docker -H 192.169.1.202:3562 -d &
# to connect to this network port
export DOCKER_HOST='tcp://192.169.1.202:3562'
</code>
where -d is deamonize 
& is for getting our command prompt back
then docker runs on 3562 port and we can check using netstat -tlp

Hint:: Remember sockets are bind to permissions like users, and groups
but network port are independent