---
layout: post
title: Basic Understanding of Railtie in Rails for Newbies
date: 2015-07-09 19:40:24.000000000 +05:30
---
Railtie is simply a class built by rails developers. 

How it will help us is like we can extend and write own methods in it, then those methods gets available to rails application

Everything in rails is a pack of gems where everything includes within Rails::Railtie. Suppose say

* Action Mailer
* Action Controller
* Active Record
* Action View


Railtie is mainly needed if you want to talk with rails configurations, rails helpers (Creating our own helpers, reuse our own helpers), extending models ( make our own macros available in models ). 


With Railtie, we can 

 * Extend our methods
 * Initialize our methods

If you want to extend then you need to use <code>Railtie</code> class that extend with <code>Rails::Railtie</code>
<pre>
<code class='language-ruby'>
 module MyGem
   class Rails < Rails::Railtie

    ## My class methods

   end
 end
</code>
</pre>

If you want to initialize then you need to use <code> initializer </code> block.

<pre>
<code class='language-ruby'>
 class MyRailtie < Rails::Railtie
  initializer "my_railtie.configure_rails_initialization" do |app|
    # write our own methods here
  end
end
</code>
</pre>

where <code> app</code> we can access all rails configurations

Similarly,

 * we can write rake tasks using <code> rake_tasks &block </code>
 * Create our own generators like device gem have <code> generators &block </code>


Happy coding :)
