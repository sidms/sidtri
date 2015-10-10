---
layout: post
title: Calling module prepend in ruby
date: 2015-10-10 13:34:01.000000000 +05:30
---

Recently i've heard about prepend method introduced in ruby and i'd like to share what's the necessity !

<code>prepend </code> as name suggest itself that we can prepend our desired methods before calling original once. Let me put it this way

<pre>
	<code class="language-ruby">
		class Foobar
			include ApiChecker

			def same_method
				puts "Foobar"
				super
			end
		end

		module ApiChecker
			def same_method
				puts 'Api checker'
			end
		end

		Foobar.new.same_method
		
		# Foobar 
		# Api checker

	</code>
</pre>


As you can see Checker is calling after method executes and this is normal way of method executioning and if you want to override it then you can use <code>prepend</code> instead of <code>include</code>

- This method is very handy in places where we want to prechecks some conditions before calling the target methods without aliasing method names and dump code in existing method