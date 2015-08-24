---
layout: post
title: Handle Statements in Ruby
date: 2015-07-08 10:46:23.000000000 +05:30
---
As we know that ruby does'nt have statements, only Expressions. So, we'll look at how to handle statements when we've encounter such cases.


Suppose say, I wanted to loop through some array collection named <code>events</code> and wanted to skip those events which will happen with in two hours from now on 

<pre>
<code class='language-ruby'>
  events = [1,2,3]
  splitters = events.collect do |event|  
   splitter(event)
  end

def splitter
  if event.time > Time.now - 2.hours
    true
  else
    return __nothing__
  end
end
</code>
</pre>

As we know we need to return something in ruby except like java, so..

<pre>
<code class='language-ruby'>
 def splitter
  if event.time > Time.now - 2.hours
    true
  else
    return nil
  end
 end

# output [true,true, nil, true, nil, true]
</code>
</pre>

As we've seen in the output we've comeup with nil's and we can remove nil's after we've get output usually and this is not good practice. Another way to approach this is to , 


<pre>
<code class='language-ruby'>
  events = [1,2,3]
  splitters = events.reject{|event| event.time < Time.now - 2.hours}.collect do |event|  
   splitter(event)
  end

def splitter
 true
end
</code>
</pre>

This way instead of asking object, we can directly ignore which doesn't match the condition.


Happy coding :)
