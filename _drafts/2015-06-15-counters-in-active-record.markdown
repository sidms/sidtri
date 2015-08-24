---
layout: post
title: Counters in Active Record
---
AR introduces counters on rails >4.2 . Let's see what counters can do

If we have Post model with votes and would like to increase/decrease votes counters can be the best way i guess

<pre>
<code class='language-ruby'>
 @post = Post.find(params[:id])
 @post.update_counters(
</code>
</pre>
