---
layout: post
title: Update Association Count Automatically using Counter Cache in Rails
date: 2015-07-03 15:15:54.000000000 +05:30
---
There are times we'll call the count on the associations.

###### Post has_many comments 

* @total_comments = Post.comments.count 

This will sql everytime we'll call count on comments.

* we'll go for <code>counter cache</code> whenever these <code>count</code> calls are more. Let's see how we can manage

For counter cache, we'll need 
 
 * To create one column on <code>post</code> table named <code>comments_count</code> where <code>comments </code> is name of association that we'll need to store count.
 * Give argument <code>counter_cache: true</code> on comments model association to tell about <code>Comment</code> model to update count whenever it'll create, update, destroy

<pre>
<code class='language-ruby'>
 class Post < ActiveRecord::Base
  # create comments_count column
  has_many :comments
 end

 class Comment < ActiveRecord::Base
   belongs_to :post, counter_cache: true
 end
</code>
</pre>

And that's pretty much it.

<pre>
<code class='language-ruby'>
 @post = Post.first
 @comment = @post.comments.new(permit_params)
 # It'll create two sql queries one for creating comments and one to update count on post model
 
 #Retrieve comments
 @post.comments_count # 1
</code>
</pre>



Happy coding :)
