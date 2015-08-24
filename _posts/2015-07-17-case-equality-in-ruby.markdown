---
layout: post
title: Case Equality In Ruby
date: 2015-07-17 23:07:56.000000000 +05:30
---
As you may already know that <code>===</code> ( Case Equality ) has some difference between  <code>==</code>. Lets see what that is.

Case Equality behaves like normal equality checker but it'll do a little more for us

<pre>
<code class='language-ruby'>
1 == 1 #true
1 === 1 #true
(1..5) === 3 #true
3 === Integer #true
3 === String #false
</code>
</pre>


As you've seen this is useful at <code>case</code> statement

Case statement in ruby operates using <code>case equality </code> unlike <code>if</code> statement.

<pre>
<code class='language-ruby'>
 case 3
  when Integer
    "This is integer"
 end
</code>
</pre>

Happy coding :)
