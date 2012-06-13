# Notes for upcoming Ruby meetup #

## Rough draft of things we are going to talk about ##

* What is Ruby?

  Ruby is a object oriented programming language deeply inspired by Smalltalk, Lisp & Perl.
  It is also a dynamically but strongly typed language.
  
* A word about dynamically languages.

  Dynamically typed means you do not declare type for your variables,
  method declarations etc during writing code.
  
  But ruby is not just a dynamically typed language but it is a 
  dynamic programming language, which means you can add new code,
  extend objects/classes, add new types at runtime.
  
* A word about strongly typed language

  Javascript:
  
        1 + "Hello" => "1Hello"
    
  Ruby:
    
        1 + "Hello" => TypeError: String can't be coerced into Fixnum
    
  A way to get around Ruby error:
  
        class Fixnum; def +(other); "#{self}#{other}"; end; end
    
  Javascript:
  
        [cow, hen,python].collect_milk => 3 litre of milk
    
  Ruby:
  
        [cow,hen,pyhton].collect_milk => DumbassError: can't milk a hen
    

   Unlike a statically typed language, strong typing is not built
   into the language and it is more of a Ruby way of doing things.
   
   Avoid automatic type coercian.
   
* Object & Classes

  Everything in Ruby is a object. Which means integer `1` is a object
  as much is your instance of `User` class. Methods are objects,lambdas
  are objects,blocks are objects, classes are objects, modules are objects.

  Even code that you write is stored as objects although you don't have
  a direct handle to them.

* Creating a class and instantiating it:

        class Car
        end
    
        car1 = Car.new()
    
* Modules and using them
  A Module is a collection of methods and constants. 
  The methods in a module may be instance methods or module methods. 
  Instance methods appear as methods in a class when the module is included, module methods do not.    
    
* In 1.9, Parent class of all classes is `BasicObject` but in Ruby 1.8 it used to be
  `Object` class. In 1.9 `Object` class sits one level below `BasicObject` class and most
  important difference between two is `Object` class includes `Kernel` module whereas
  `BasicObject` class does not.
  
  For more information:
    http://www.ruby-doc.org/core-1.9.3/BasicObject.html
    
* Duck Typing:

    
        animals = [Cow.new(),Goat.new()]
        
        def collect_milk(animals)
          milk = []
          animals.each do |animal|
            if animal.respond_to?(:milkit)
              milk << animal.milkit
            else
              raise DumbassError.new("Cant milk #{animal.inspect}")
            end
          end
          milk
        end


  Duck typed and yet strongly typed. Why? - why can't we just ignore
  animals that can't be milked?
  

