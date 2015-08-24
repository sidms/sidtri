---
layout: post
title: validating passenger
---
validate the install by running sudo passenger-config validate-install. For example:

sudo passenger-config validate-install
 * Checking whether this Phusion Passenger install is in PATH... ✓
 * Checking whether there are no other Phusion Passenger installations... ✓
All checks should pass. If any of the checks do not pass, please follow the suggestions on screen.

Finally, check whether Nginx has started the Passenger core processes. Run sudo passenger-memory-stats. You should see Nginx processes as well as Passenger processes. For example:

Copy$ sudo passenger-memory-stats
Version: 5.0.8
Date   : 2015-05-28 08:46:20 +0200
...

---------- Nginx processes ----------
PID    PPID   VMSize   Private  Name
-------------------------------------
12443  4814   60.8 MB  0.2 MB   nginx: master process /usr/sbin/nginx
12538  12443  64.9 MB  5.0 MB   nginx: worker process
### Processes: 3
### Total private dirty RSS: 5.56 MB

----- Passenger processes ------
PID    VMSize    Private   Name
--------------------------------
12517  83.2 MB   0.6 MB    PassengerAgent watchdog
12520  266.0 MB  3.4 MB    PassengerAgent server
12531  149.5 MB  1.4 MB    PassengerAgent logger
...








..........................





.2 Login to your server, create a user for the app

Login to your server with SSH:

Copy$ ssh adminuser@yourserver.com
Replace adminuser with the name of an account with administrator privileges or sudo privileges.

Starting from this point, unless stated otherwise, all commands that we instruct you to run should be run on the server, not on your local computer!
Now that you have logged in, you should create an operating system user account for your app. For security reasons, it is a good idea to run each app under its own user account, in order to limit the damage that security vulnerabilities in the app can do. Passenger will automatically run your app under this user account as part of its user account sandboxing feature.

You should give the user account the same name as your app. But for demonstration purposes, this tutorial names the user account myappuser.

Copy$ sudo adduser myappuser
We also ensure that that user has your SSH key installed:

Copy$ sudo mkdir -p ~myappuser/.ssh
$ sudo sh -c "cat $HOME/.ssh/authorized_keys >> ~myappuser/.ssh/authorized_keys"
$ sudo chown -R myappuser: ~myappuser/.ssh
$ sudo chmod 700 ~myappuser/.ssh
$ sudo sh -c "chmod 600 ~myappuser/.ssh/*"
2.3 Install Git on the server

Debian, Ubuntu	
Copysudo apt-get install -y git
Red Hat, CentOS, Fedora, Scientific Linux, Amazon Linux	
Copysudo yum install -y git
Other operating systems	Please install Git from git-scm.com.
2.4 Pull code

You need to pick a location in which to permanently store your application's code. A good location is /var/www/APP_NAME. Let us create that directory.

Copy$ sudo mkdir -p /var/www/myapp
$ sudo chown myappuser: /var/www/myapp
Replace myapp and myappuser with your app's name and your app user account's name.

Now let us pull the code from Git:

Copy$ cd /var/www/myapp
$ sudo -u myappuser -H git clone git://github.com/username/myapp.git code
