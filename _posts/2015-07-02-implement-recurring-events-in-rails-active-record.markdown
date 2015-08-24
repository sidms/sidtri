---
layout: post
title: Implement Recurring Events in Rails Active Record
date: 2015-07-02 15:53:19.000000000 +05:30
---
Rails 4 comes with default support for hstore and in Postgresql we can insert arrays, hashes also. So why are you waiting for and dependent on some gems to make things work. Let go dive into some unique stuff

We'll use Postgresql Datatypes here

 * Array
 * Hstore


Suppose say you have blog post and you wanted to implement taggings for it, right away we'll think  <code> has_many </code> relationship. But with postgresql array type we achieve easily.

<pre>
<code class='language-ruby'>
  class Post < ActiveRecord::Base
    
  end 
  
 # migration 
  t.string 'tags', array: true

 @post = Post.new
 @post.tags # []
 @post.tags = ['ruby', 'rails']
 @post.save
  
 Post.first.tags # ['ruby', 'rails']
</code>
</pre>

Dont forget to index tags

###### Query

 <pre>
  <code class='language-ruby'>
 class Post < ActiveRecord::Base
     scope :any_tags, -> (tags){ where('tags && ARRAY[?]', tags) }
     scope :all_tags, -> (tags){where('tags @> ARRAY[?]', tags)}
   end

   Post.any_tags('ruby') 
   # Post tags='ruby,rails'/>
  </code>
 </pre>

So, with help of array type we can implement recurring events easily.

Suppose say we have <code>Event</code> model and we'll create event with start_time, end_time. 

Using <code>Icecube</code> gem if you provide start time and end time it'll provide dates that matching the event according to the recurring condition given.

I've implemented simple service that'll give between dates when we give our model.

<pre>
<code class='language-ruby'>
 class FpCube
	def initialize(event)
	  @event = event
	  @schedule = IceCube::Schedule.new(now = @event.date) do |s|
  	s.add_recurrence_rule(IceCube::Rule.weekly)
    end

    def between_dates
     @schedule.occurrences(@fpclass.expiry)
	end
 end
</code>
</pre>  

Using above service we'll get <code> between dates </code> and we'll store these dates in out database model event using Postgres array type like below.

<pre>
<code class='language-ruby'>
 class Event < ActiveRecord::Base
   before_save :search_dates
   scope :any_events, -> (date){ where('dates && ARRAY[?]', dates) }

   def search_dates
      self.dates = FpCube.new(self).between_dates
   end 
 end

 # Search if any events today
 Event.any_events(Date.today)
</code>
</pre>


This is flexible way of handling recurring events in rails. Our service <code> Fpcube </code> only implements for weekly recurring. You can check docs for more .


Happy coding :)

[Reference](http://edgeguides.rubyonrails.org/active_record_postgresql.html) 
