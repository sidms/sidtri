---
layout: post
title: Usage of calling StringIO
date: 2015-11-09 13:34:01.000000000 +05:30
---

Creating strings using class StringIO instead of String gives us string that behave like IO. Simply saying that the returned string have some extra methods called <code>gets</code>,<code>puts</code>,<code>read</code> etc.,
Handy using StringIO and injecting instead of reading from a actual file from disk.

<pre>
	<code class='language-ruby'>
		io_string = StringIO.new('Hi there')
		=> #<StringIO:0x007feacb0cd4e8>
		io_string.gets
		=> "Hi there"
		io_string.puts 'see you later'
		=> nil
		io_string.rewind
		=> 0
		io_string.read
		=> "Hi theresee you later\n"
	</code>
</pre>

IO objects are created in ruby using streams symlinks called <code>0, 1, 2</code> that exists at <code>/dev/fd</code>, where 0 is for reading, 1 is for writing and 2 is for error(Standard Error).

Global variables <code>$stdin</code>, <code>$stdout</code> and <code>#stderr</code> points to these streams by default in ruby

<pre>
	<code class='language-ruby'>
		$stdin.puts 'Hi there'
		#same as $> puts 'hi there'
	</code>
</pre>

Want to learn more about IO objects, sockets(which inherit from IO objects) refer [here](http://www.linusakesson.net/programming/tty/)

FYI: Remember eventhough StringIO objects have methods like IO objects, StringIO doesnt inherit from IO class.
