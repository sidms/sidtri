---
layout: post
title: Template Method Pattern in Ruby
date: 2015-06-29 21:33:03.000000000 +05:30
---
How dry our code is, how better it is stable secure, flexible. So we need to make our code super dry. Patterns are some rules that'll help us build code in a structural manner to reduce complexity and increase flexibility.

We'll go old school on example about dogs, cats and mammals

<pre>
<code class='language-ruby'>
 class Mammal 
 attr_reader :legs, :eyes
  def bones?
   true
  end
 end

 class Dog < Mammal
  def initialize(legs, eyes)
    @legs = legs
    @eyes = eyes
  end
 end

 class Man < Mammal
  def initialize(legs, eyes)
    @legs = legs
    @eyes = eyes
  end
 end 

 @man = Man.new(2, 2)
 @man.legs # 2

 @dog = Dog.new(4, 2)
 @dog.legs # 4 
</code>
</pre>

Dont you think is that necessary to get legs, and eyes while initializing. This is where <code>template method pattern</code> is applicable.

<pre>
<code class='language-ruby'>
 class Mammal 
 attr_reader :legs, :eyes
  def bones?
   true
  end
 end

 class Dog < Mammal
  def initialize
    @legs = my_legs
    @eyes = my_eyes
  end

  def my_legs
    4
  end

  def my_eyes
   2
  end
 end

 class Man < Mammal
  def initialize
    @legs = my_legs
    @eyes = my_eyes
  end
  def my_legs
    2
  end
 
  def my_eyes
   2
  end
 end 

 @man = Man.new
 @man.legs # 2

 @dog = Dog.new
 @dog.legs # 4 
</code>
</pre>


Remember like this, the code we are dealing is inheritance and this pattern is applicable while in these cases itself.
Because for inheritance one subclass has some state and another subclass has another state, instead of passing that state while initializing we can directly make it available in that class itself and get while initializing.

The methods we've written for dog and cat are called <code>stubs</code>.

Note:: 

 We can still reduce the above code and make it much <code>dry</code>.

<pre>
<code class='language-ruby'>
 class Mammal 
 attr_reader :legs, :eyes
  def initialize
    @legs = my_legs
    @eyes = my_eyes
  end

  def bones?
   true
  end
 end

 class Dog < Mammal
  def my_legs
    4
  end

  def my_eyes
   2
  end
 end

 class Man < Mammal
  def my_legs
    2
  end
 
  def my_eyes
   2
  end
 end 

 @man = Man.new
 @man.legs # 2

 @dog = Dog.new
 @dog.legs # 4 
</code>
</pre>


Happy coding :)
