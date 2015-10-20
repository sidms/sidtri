---
layout: post
title: Dependency Inversion with Inversion of Control
date: 2015-10-20 13:34:01.000000000 +05:30
---


Today i'd like to talk about D - principle that uncle bob come up with in SOLID OOP principles   

Inversion of control as name suggest that instead of having application call methods in a framework, the framework calls implementations provided by the application. Assigning dependencies at runtime, rather than statically referencing dependencies at each level.

Dependency inversion is kind of inversion of control, where dependencies are passed as a parameters, or at contruction level.


Suppose we have two classes (Movie, JSONFormatter)
<pre>
  <code class='language-ruby'>
    class Movie
      def initialize
        @moviegoers = []
      end

      def <<(moviegoer)
        @moviegoers << moviegoer
      end


      def list
        JSONFormatter.new.to_s(@moviegoers)
      end
    end


    class JSONFormatter
      def to_s(list)
        list.to_json
      end
    end
  </code>
</pre>

 Movie has many moviegoers and if we want to see list of moviegoers after movie ended and call list. But you clearly sees that list method is hardcoded with one format called JSONFormatter and if we want to print in different format then we cannot do right above.


 You can also identify this as this movie class depends on another class called JSONFormatter. We should eliminate one class depends on another as suggest by rule called SINGLE RESPONSIBILITY PRINCIPLE (One class one goal). So by using Dependency inversion we can rewrite this as below. 

<pre>
  <code class='language-ruby'>
    class Movie
      def initialize
        @moviegoers = []
      end

      def <<(moviegoer)
        @moviegoers << moviegoer
      end


      def list(formatter = JSONFormatter.new)
        formatter.to_s(@moviegoers)
      end
    end


    class JSONFormatter
      def to_s(list)
        list.to_json
      end
    end

    class HTMLFormatter
      def to_s(list)
        list.to_html
      end
    end
  </code>
</pre>


By implementing like above Movie class doesn't depends on other classes and we can happily inject objects at run time. This gives us flexibility to call methods and code clean. Happy coding :)
