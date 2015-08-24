---
layout: post
title: Adding Custom Flash Types In Rails Controllers
date: 2015-06-20 18:13:06.000000000 +05:30
---
Except for <code>notice</code> whenever we want to create other flash types we need to assign that to flash array like below

<code>flash[:warning] = "Go for cycling" </code>

Instead of doing all this we can assign our custom flash types at base controller using 

<pre>
<code class="language-ruby">
class ApplicationController < ActionController::Base
  add_flash_types :warning
end

# in your controller
redirect_to user_path(@user), warning: "Incomplete profile"

# in your view
<%= warning %>
</code>
</pre>


Where <code>add_flash_types</code> is a class method on ActionController::Flash 
