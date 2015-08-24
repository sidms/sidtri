---
layout: post
title: Rails Convention Over Configuration
date: 2015-06-27 09:03:33.000000000 +05:30
---
* Rails `User` model matches `users` table in database
* Rails Controller names matches with views for rendering


As you've seen above scenario's as it spreads mostly in rails, i'd like to say it has some name what we've called Convention Over Configuration.

Not only in above scenarios, rails will follow this pattern everywhere.

We should learn something from rails that we should also follow this `COC` while writing code in rails/wherever to make our code lot more flexible.

Let's suppose say that we want to map our models from params we're getting at controller

<pre>
<code class='language-ruby'>
 class UsersController < ApplicationController
  
  def show
   # params = {:name => 'customer'}
   @user = User.find(params[:name])
   @role = figure_out_role_class
  end
   
  private
    def figure_out_role_class
      case params[:name] 
      when "customer" 
          @user.customer
      when "partner"
          @user.partner
      when "admin"
          @user.admin
      else
          raise "Please make sure role given exists with us"
      end
    end
 end
</code>
</pre>

Good programmers will mostly eliminate case/if statements because it follows `Tell Dont Ask` Pattern. So we'll remove case statement and lets see how best we can do.

<pre>
<code class='language-ruby'>
 class UsersController 
  private
   def figure_out_role_class
     @user.send(params[:name])
   end 
 end
</code>
</pre>

Using `send` method, we can pass string or symbols as methods.

Note:: 

* If for suppose you're in need to find Model itself, you can achieve using `classify.constantize`

<pre>
<code class='language-ruby'>
 # params[:name] = "customer"
 
 params[:name].classify # "Customer"
 params[:name].classify.constantize 
 # Customer(id: integer, email: string, ...)

 params[:name].classify.constantize.new # initialization
 # Customer id:nil, email: nil > 
</code>
</pre>


Happy coding :)
