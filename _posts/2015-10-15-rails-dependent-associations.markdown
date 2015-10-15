---
layout: post
title: Rails dependent association
date: 2015-10-10 13:34:01.000000000 +05:30
---

 Before we talk about dependent option it is important us to understand
 the difference between destroy and delete.

 destroy will execute callbacks ( something called event listeners that
 we can hook into active record models and those will trigger depends on
 the condition we provided ) before destroying object while delete will not give damn about what callbacks that exists within that object and directly goes for it.

 Simply says destroy will kills his children and his grand children if
 he dies.

 Delete will leave his children and grand children as they were even if
 she dies.


Dependent is the option we provide while creating associations in active
record where it controls dependencies for particular object when it gets
destroyed.

<pre>
<code class='language-ruby'>
  class Post < ActiveRecord::Base
    has_many :comments, dependent: :destroy

  end
</code>
</pre>

Dependent has around five options that we can pass

* destroy -> destroys ( callback executes on associated objects as well
) all comments that post belongs to
* delete_all -> delete ( callbacks will not execute on comments objects
) all comments that post belongs to 
* nullify -> makes foreign key for comments objects set to nul
* restrict_with_error -> Error raises if any associated objects

* For has_and_belongs_to_many association delete and destroy are same
because of the join table.

* If no dependent is provided then default strategy ( common behaviour )
  is it doesnt give damn to their associated objects ( here comments )
  and leaves foreign key as it is

  <pre>
  <code class='language-ruby'>
  class User < ActiveRecord::Base
   has_many :comments 

   end

   class Post < ActiveRecord::Base
    has_many :users, through: :comments

   end
  </code> 
  </pre>

  Here in post i've used through association for each post i have many
  commented users list.

  For through association the default strategy slightly varies from
  "doesnt give damn" to "delete_all"


  Happy coding :)

