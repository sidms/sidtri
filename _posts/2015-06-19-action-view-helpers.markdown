---
layout: post
title: Useful Action View Helpers
date: 2015-06-19 18:36:54.000000000 +05:30
---
##### capture(*args)

The capture method can be used in ERB templates

<pre>
<code class='language-ruby'>
<% @greeting = capture do %>
  hello there, at <%= Time.now %>
<% end %>
</code>
</pre>

You can then use that variable anywhere else. For example:
<pre>
<code class='language-ruby'>
  <boldtag><%= @greeting %></boldtag>
</code>
</pre>


##### Concat
print and puts will print on console but concat method will be useful if you want to print anything on html itself. 

useful when we are generating html in non erb files
<pre>
<code class='language-ruby'>
<% concat "hello" # is the equivalent of <%= "hello" %>
</code>
</pre>


##### content tag, content tag for
Assigns unique html id for every loop, which is useful to identify when required.
<pre>
<code class='language-ruby'>
 <%= content_tag_for(:tr, @person) do %>
  <td><%= @person.first_name %></td>
  <td><%= @person.last_name %></td>
<% end %>
</code>
</pre>

##### Raw
Outputs html code without escaping and converting into complete useless string.

##### Safe Join

Suppose we have two html tags from concat or capture methods and we'd like to join them both, we use safe join
<pre  class='language-markup'>
<code language='language-markup'>
 safe_join(["&lt;p&gt; foo &lt;/p&gt;".html_safe, "&lt;p&gt; ba &lt;/p&gt;"], "br /")
 # => "p foo /p&lt;br /&gt;&lt;p&gt;bar&lt;/p&gt;"
</code>
</pre>


Happy Hacking..
