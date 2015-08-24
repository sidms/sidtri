---
layout: post
title: Make Backup and Restore Postgresql Database Using Simple Commands
date: 2015-07-04 18:53:30.000000000 +05:30
---
Today, we'll talk about how to create backup file and restore from it in postgresql.


Postgresql as we know that it works on roles, 

* Go to <code> postgres</code> user
 <pre>
 <code class='language-ruby'>
  sudo su postgres # where postgres is user name 
 </code>
 </pre>

* Create backup folder in root to store all backup files 
 <pre>
 <code class='language-ruby'>
  >> cd .. 
  >> mkdir backups
 </code>
 </pre>
* create backup using gzip
<pre>
 <code class='language-ruby'>
  pg_dump current_database_name | gzip > ~/backup/file_name.gz
 </code>
 </pre>

* Create fresh database to dump <code> file_name.gz </code>
<pre>
 <code class='language-ruby'>
  psql -c "create database new_database_name;"
 </code>
 </pre>

* Dump <code> file_name.gz</code> to <code> new_database_name </code> database
<pre>
 <code class='language-ruby'>
  gunzip -c ~/backup/file_name.gz | psql new_database_name
 </code>
 </pre>


Gunzip will create migrations, and dump data to new database. So we now have perfect cloned version.


Happy coding :)



