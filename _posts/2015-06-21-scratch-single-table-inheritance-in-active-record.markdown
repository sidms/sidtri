---
layout: post
title: Scratching Single Table Inheritance (STI) in Active Record
date: 2015-06-21 20:24:44.000000000 +05:30
---
In my recent application i come up with three roles of authentication 

* Customer
* Partner
* Admin

As you may hear about mammals, dogs, cats story from c, java etc., and we've learnt creating some inheritance pattern with mammal as super class. Single Table Inheritance is a pattern that we can apply this same kind of inheritance in Active Record and here it is how...


<pre>
<code class='language-ruby'>
class Customer < User; ;end
class Partner < User; ;end

class User < ActiveRecord::Base
 attr_accessor :first_name, :last_name, :age, :email
end

</code>
</pre>

Oh! i forgot to include <code>type</code> as it is required to fetch results and guess what, rails will automatically takes care of creating type value while we are creating or initializing <code>Customer</code> `Partner` `Admin`. Let's see results

<pre>
<code class='language-ruby'>
@customer = Customer.create(:name => 'sid', :age => '18')
@partner  = Partner.create(:name => 'sourabh', :age => '24')

@customer.user 
# User name='sid' age='18' type='customer'>

@partner.user
# User name='sourabh' age='24' type='partner'>
</code>
</pre>

So, by using single table inheritance we'll maintain single table with multiple roles. 

Happy coding :)
