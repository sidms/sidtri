---
layout: post
title: Redis Cheatsheet
date: 2015-07-16 16:23:45.000000000 +05:30
---

Redis is key-value store. Lets see Redis types below

* Lists
* Sets
* Sorted Sets
* Hashes


Installation :: [Click here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)

###### Lists

Lists are nothing but arrays 

* Add end of array <code> RPUSH array_name 'value' </code>
* Add at beginning of array <code> LPUSH array_name 'value' </code>
* Fetch <code> LRANGE array_name 0 n </code> , where <code> n </code> is range. 


###### Sets 
Sets are similar to arrays, but we can say un ordered arrrays

* Add <code> SADD set_name 'value' </code>
* Check value exists <code> SISMEMBER set_name 'value' </code> . Returns 0 or 1
* Fetch  <code> SMEMBERS set_name </code>
* Check for union values from two sets <code> SUNION set_name1 set_name2 </code>

###### Sorted Sets
As name suggest with these sorted sets we can send score along with value 

 * Add <code> ZADD set_name score 'value' </code>
 * Fetch <code> ZRANGE set_name 0 n </code>, where n is range


###### Hashes
To store hash of data, like normal table columns in relational databases we'll use hashes in Redis

* Add <code> HMSET hash_name:id columnName 'value' columnName 'value' </code>
* Add <code> HSET hash_name:id columnName 'value' </code>, <code> HSET hash_name:id columnName 'value' </code>

* Fetch <code> HGETALL hash_name:id </code>

<pre>
<code language='ruby'> 
    HSET user:1000 visits 10
    HINCRBY user:1000 visits 1 => 11
    HINCRBY user:1000 visits 10 => 21
    HDEL user:1000 visits
    HINCRBY user:1000 visits 1 => 1
</code>
</pre>

* Increment <code> HINCRBY set_name:id column_name increment_count</code>

