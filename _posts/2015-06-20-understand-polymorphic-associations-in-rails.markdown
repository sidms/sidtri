---
layout: post
title: Understanding Polymorphic Associations in Rails
date: 2015-06-20 22:16:23.000000000 +05:30
---
I'm lazy to write good article instead i point out what's inside it directly, and as i know that we are too lazy to read articles too because ruby makes us lazy :)

Did you read previous article about [STI](/scratch-single-table-inheritance-in-active-record/) (Single table inheritance ) ? Because these are mostly related.

Okay i come to point, Why do we use polymorphic associations ? 

Suppose assume that you have your own website with `articles` and `forumposts` and if you'd like to implement `comments` for both of those. This is where polymorphism comes. 

I didnt understand ..! 

Okay, let me explain in detail

 Forumposts contains comments right.. 
 Articles contains comments too right...

So, `comments` belongs to `forumposts` and `articles`, and we'll use polymorphic associations when a model can belong to more than one other model.

Before implement polymorphism i'll show what we achieve at end
<pre>
<code class='language-ruby'>
@article = Article.first
@article.comments 
 # comment content='nice article' whatever_id='1' whatever_type='article'>

@post = Forumpost.first
@post.comments
 # Comment content='nice post' whatever_id='2' whatever_type='forumpost'>
</code>
</pre>


Polymorphic needs
 
* whatever_id
* whatever_type 

It'll store polymorphic class name in `whatever_type` i.e., either 'article' or 'forumpost' in our case. 

<pre>
<code class='language-ruby'>

rails g migration AddCommentableIdToComments commentable_id:integer commentable_type:string

 class Comment < ActiveRecord::Base
  belongs_to commentable, polymorphic: true
 end

 class Article < ActiveRecord::Base
  has_many :comments, as: :commentable
 end

 class Forumpost < ActiveRecord::Base
   has_many :comments, as: :commentable
 end
</code>
</pre>


In STI we used only one table to get similar kind of results and in here we used many tables and one can be used based on situation.


###### Routes

<pre>
<code class='language-ruby'>
 resources :articles do
  resources :comments, module: :articles
 end

 resources :forumposts do
  resources :comments, module: :forumposts
 end
</code>
</pre>

###### Views

== _comment.html.erb ==
<pre>
<code class='language-ruby'>
 h6> comments
  % commentable.comments.each do |comment|
</code>
</pre>


== article > show.html.erb ==
<pre>
<code class='language-ruby'>
 h6> comments
  % render :partial => 'comunderstand-polymorphic-associations-in-rails/ments', locals: { commentable: @article}
</code>
</pre>

== forumpost > show.html.erb ==
<pre>
<code class='language-ruby'>
 h6> comments
  % render :partial => 'comments', locals: { commentable: @forumpost}
</code>
</pre>


Happy coding :)
