---
layout: post
title: Using merge to Extend Scopes in Active Record Rails
date: 2015-06-23 22:53:23.000000000 +05:30
---
We can call available books from author and we can use scopes that present in book model directly using simple `merge` method.

<pre>
<code class='language-ruby'>
class Book < ActiveRecord::Base
  scope :available, where(:available => true)
end

class Author < ActiveRecord::Base
  has_many :books
  scope :with_available_books,joins(:books).merge(Book.available)
end

# Return all authors with at least one available book:
Author.with_available_books

end

</code>
</pre>

This makes use of scopes calling as many times we want from other models too without redefine entire stuff again.
