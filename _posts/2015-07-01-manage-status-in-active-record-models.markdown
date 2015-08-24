---
layout: post
title: Manage Status in Active Record Models
date: 2015-07-01 22:20:51.000000000 +05:30
---
Hey, 

We all know that sometimes we needs to implement status of our models. Suppose say if we take <code>orders</code> model for cart, every order has got state. 

<pre>
<code class='language-ruby'>
 class Order < ActiveRecord::Base
   STATUSES = ['pending', 'approved', 'waiting', 'declined']
  
 end

 Order.new(:status => 1) # approved
</code>
</pre>

Using constant <code>STATUSES</code> we'll get order status in a human readable way.

But there is a better approach for these kind of things, lets see how


<pre>
<code class='language-ruby'>
 class Order < ActiveRecord::Base
  enum status: [ :pending, :approved, :rejected ]
  
 end

</code>
</pre>

What comes with it ? 

Guess what, we get predefined methods <code>pending?</code> <code>approved?</code>. Lets check this

<pre>
<code class='language-ruby'>
 Order.first.status # pending
 Order.new.status = "pending"

 # Set default value at migration 
 t.column :status, :integer, default: 0, null: false
</code>
</pre>


One problem is that we cannot use these human names while searching

<pre>
<code class='language-ruby'>
 Order.where('status=?', 'pending') # Error raises
</code>
</pre>



Enum is not a feature in ruby, but rails 4.1 introduced it.

Happy coding :)



