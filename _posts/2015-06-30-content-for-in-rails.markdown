---
layout: post
title: Content For in Rails
date: 2015-06-30 20:33:45.000000000 +05:30
---
Content for behaves 

 * Merge and output content ( without block )
 * Assign Content ( if you pass block )

Confused ?  Let me explain

<pre>
<code class='language-ruby'>
  content_for :identifier do 
    "<html><head></head><body>Hi</body></html>"
  end

  # It'll store all content in identifier. We can call this identifier using content_for or yield tag

 content_for :identifier # <html><body>Hi</body></html>
 yield :identifier # <html><body>Hi</body></html>
</code>
</pre>

Sometimes it is required to call content on helpers and we cannot get data from <code>yield</code>. We can simply use content_for :identifier to get data

<pre>
<code class='language-ruby'>
 module IdentifierHelper
  def identify
    content_for(:identifier)
  end 
 end
</code>
</pre>


Suppose say we are having common navigation for different pages and we want to pass content on navigation from each partial, or each inner html, we can achieve using content_for

<pre>
<code class='language-ruby'>
  # index.html.erb
  
  content_for :box_count do
    "3"
  end

 # show.html.erb
   content_for :box_count do
    "0"
   end 

 # _nav.html.erb
   yield :box_count
</code>
</pre>


Happy coding :)

