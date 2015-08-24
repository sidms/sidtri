---
layout: post
title: Why to use Structs in Ruby ?
date: 2015-06-14 16:10:18.000000000 +05:30
---
Structs will let us creates a classes without much code, so that we can initialize them and use wherever we want

Check this out

<pre>
<code class='language-ruby'>
 Developer = Struct.new(:name, :age, :language)
  
 @developer = Developer.new("sid",23, "ruby")
</code>
</pre>

If you have any custom methods like <code> user.full_name </code>, we can easily achieve this by passing block on struct. Check this out!

<pre>
<code class='language-ruby'>
 User = Struct.new(:first_name, :last_name, :age) do 
  def full_name
   "#{first_name} #{last_name}"
  end
 end
  
 @user = User.new("sai","tej", "19")
 @user.full_name # sai tej
</code>
</pre>
