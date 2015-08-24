---
layout: post
title: Refactoring using Extract Method
date: 2015-06-22 21:47:02.000000000 +05:30
---
Assume these below conditions 

* I want to notify that one of my branch in my bank is getting closed
* I'm getting some data in hash form contains bank id
* I want to find `Depositors` from the bank id
* I want to send them all text messages that our branch is closing

<pre>
<code class='language-ruby'>
class SendNotification

def self.perform(data)

 @bank = Database.find(data[:bank_id])
 @users = @bank.users

 @users.each do |user|
  SMS.notify(user)
 end

rescue 
 ErrorHandler
end
end

</code>
</pre>


 First thing to note is that it violates the single method single rule pattern. As we are seeing that `perform` method is doing a lot of things instead what it needs to do. 

Is there any other problem...? Ofcourse there is, as we've seen `perform` method is class method.

Whats wrong with class method ?  

Remember classes are also objects in ruby so objects contain methods and assume in the above example that SendNotification, our need is to call this by sending different data each time to perform action and so, one object should conflict other object state because we are not creating any objects while calling bank.perform.

We can easily refactor this by creating separate object each time `perform` class method is called and by using Extract method techniques.

<pre>
<code class='language-ruby'>
 class SendNotification

   def self.perform(data)
    new(data).perform
   end
   
   def initialize(data)
     @data = data
   end

   def perform
     bank.users.each do |user|
       SMS.notify(user)
     end
     rescue 
       ErrorHandler
   end
  
  private
    def bank
     @bank = Database.find(data[:bank_id])
    end
end


## Output
bank1 = SendNotification.perform(bank_id: 1)
bank2 = SendNotification.perform(bank_id: 2)
</code>
</pre>


As you can see that eventhough `perform` is class method the object it interact with is different for each time we've called `SendNotification` class.

* We've removed long method into short methods 
* Duplication code is reduced, by making behaviour easier to reuse.
* Followed single responsibility principle

By these above points we can say that we've followed Extract method pattern.



Happy coding :)
