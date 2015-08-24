---
layout: post
title: Digging into Active Record Where method
date: 2015-06-19 19:09:11.000000000 +05:30
---
<code> Where </code> is active record query method that'll query sql according to the provided database adapter.

<pre>
<code class='language-ruby'>
 User.where
 # ActiveRecord::QueryMethods::WhereChain:0x007f5010e35690
 @scope=
  [# User id: 1, login: nil, first_name: nil, last_name: nil, crypted_password: 
   # User id: 2, login: nil, first_name: nil, last_name: nil, crypted_password: ...]

# ActiveRecord::QueryMethods::WhereChain has only one instance method, i.e., not

User.where.not('string', 'array', 'hash')
</code>
</pre>

So we cannot ping `includes`, `joins`  on above query because these methods belongs to `ActiveRecord::QueryMethods` not `WhereChain`. But if we do write `where('...')` condition then we can ping `includes` `joins` eventhough `where('...')`  condition returns array.

So what i conclude is that active record intelligence will not query the results until it'll fetch all of them. So we can use as many where methods we want without breaking the `law of demeter`

By the above theory it clearly explains that we can use `Joins`, `Includes` before or after where query

<pre>
<code class='language-ruby'>
User.where('first_name=?', 'sid').joins(:customer) 

User.joins(:customer).where('first_name=?','sid')

# Both above methods will give us same result 
</code>
</pre>

###### Where Parameters

*string*

*Array*

* Eg:: ([first, second, third])
* First is template
* where(['? ?', 'first question', 'second question'])

*Hash*

* Keys are treated as fields
* User.where({ name: ["Alice", "Bob"], age: 22})
* == Polymorphic belongs_to==

*Joins*

* User.joins(:posts).where({ posts: { published: true } })


Note:: 
One last thing i want to conclude is that, observe this below method

<pre>
<code class='language-ruby'>
User.where('first_name=?','sid')
</code>
</pre>

Wait what ? it doesnot belongs to strings, arrays or hashes as you explained in parameters. 
Dont worry, What i want to say again is that its Active record intelligence and it'll assume that above one as array parameter as below 
<pre>
<code class='language-ruby'>
User.where(['first_name=?', 'sid'])
# Remember first argument is template
</code>
</pre>

Happy coding :)
