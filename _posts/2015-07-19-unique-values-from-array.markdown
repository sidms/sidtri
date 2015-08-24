---
layout: post
title: Unique Values From Array in Ruby
date: 2015-07-19 20:18:34.000000000 +05:30
---
Recently i worked on something and i came up with uniq! method and i'm posting here because it's feels like i know it, but i need to know a little more.

####### Usage

* uniq
* uniq!

<code> uniq </code>

Simply returns a new array by removing duplicates.

<pre>
<code class='language-ruby'>
 a = [ "a", "a", "b", "b", "c" ] 
 a.uniq   # => ["a", "b", "c"]
</code>
</pre>

Suppose say we have 
<pre>
<code class='language-ruby'>
  data = [{:a => 1, :b => 2},\
          {:a => 1, :b => 1},\
          {:a => 2, :b => 2},\
          {:a => 2, :b => 1}]
  # extract some unique hashes which do not repeat of values :a => 1
 data.uniq {|hash| hash[:a] }
 # [{:a => 1, :b => 2}, {:a => 2, :b => 2}]

</code>
</pre>


<code> uniq! </code>

Uniq! can give nil if no duplicates exists and can be used to validate

<pre>
<code class='language-ruby'>
 [1,2,3].uniq!
 # => nil
 [1,2,3,4,4,4].uniq!
 # => [1,2,3,4]
</code>
</pre>

