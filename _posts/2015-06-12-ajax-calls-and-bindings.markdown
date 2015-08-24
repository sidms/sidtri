---
layout: post
title: Ajax Calls and Bindings
date: 2015-06-12 13:34:01.000000000 +05:30
---
Hi there,

 There may be times you'll need to call server using dynamically through ajax, but you may face problems assigning data to variables that are in-scope.

This code as you can see below bind <code>this</code> to inner scope, so that we can assign <code>data</code> to outer scope variables.

<pre>
<code class='language-coffeescript'>
fetchposts: ->
 return $.post('url');
this.fetchposts().then(function(data){
  # this is scoped to outside
}.bind(this))
</code>
</pre>

As you can see that i've used <code>then</code> which is what we've called <code>promises</code> in javascript environment. 
<hr>
* Javascript [Bind ](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind) 
