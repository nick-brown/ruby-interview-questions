# <img src="https://upload.wikimedia.org/wikipedia/commons/7/73/Ruby_logo.svg" width="40" height="40"> Ruby Interview Questions

While typical programming interview questions may focus on problem solving, data structures, and algorithms, these questions focus on concepts specific to Ruby programming. These questions may be useful in judging a developers's experience and understanding of the Ruby language.

A significant amount of discretion should be used when using programming-language specific questions such as these since the memorizaton of core objects and methods is not necessarily indicative of a good programmer. Most of the questions here are focused on Ruby's behavior for that reason. With that in mind, an experienced Ruby developer should be able to answer the bulk of the easiest and intermediate questions.

#### Organization

The questions are listed in ascending order by their general difficulty within each section category. Questions in some sections may not be perceived as difficult at all. Remember that the perceived difficulty of these questions is highly subjective. Comprehensive answers are also provided for the understanding convenience of the reader.

#### Syntax

Standard Ruby documentation syntax is used. `::` is used to signify access to constants and class methods while `#` is used to signify access to instance methods.

#### Contributing

Meaningful contributions will be accepted. A meaningful contributions may mean any of the following:

* New questions with answers.  
* Fixes to existing questions or answers.  
* Clarification of existing questions or answers.  
* Elaboration of existing answers.

Any fixes to answers or updates to questions that make them more readable or understandable should be promptly merged. Questions that contain code should be tested before they are submitted. Remember that the meaning of these questions is to gauge an overall familiarity with Ruby concepts and behaviors, and also a general familiarity of core objects and methods. Questions about data structures and algorithms, design patterns, or other general programming questions are generally outside the scope of this document. Questions about experience, motivations, and related questions should also not be listed here. Significant contributors should be added to the list below.

* [@gregstallings](<https://twitter.com/gregstallings>)
* [@npalaniuk](<https://twitter.com/npalaniuk>)

Language Characteristics and Core Objects
-------------------------------------------------------------------------------

Q: What are the only two values that evaluate to false?  
A: `false` and `nil`

Q: Is Ruby whitespace-dependent?  
A: Sometimes.

Q: What is the highest level in the object model in Ruby 1.9+?  
A: `BasicObject`

Q: Is everything in Ruby an object?  
A: No. Methods are not objects. Blocks are not objects.

Q: Which core object includes the `Kernel` module?  
A: `Object`

Q: What can you say for sure about an identifier that begins with a capital letter?  
A: It is a constant.

Q: What does DSL stand for and why does it come up when describing Ruby?  
A: A Domain Specific Language is an API that allows you to solve a problem or represent data more naturally than you could otherwise. The flexible nature of Ruby's syntax and the ability to alias and alter existing methods and classes makes it conducive to creating DSL's.

Q: What is duck typing and how does it apply to Ruby?  
A: That an object may be acted upon even if it isn't the expected type as long as it looks and behaves like the expected object. This is a characteristic of Ruby because the lack of type checking of parameters makes this an effective programming technique.

Q: Is Ruby a statically typed or a dynamically typed language?  
A: Dynamically typed since type checking is done at runtime.

Q: Is Ruby a strongly typed or a weakly typed language?  
A: Strongly typed since an object's type is checked before an operation is performed on it.

Q: What does it mean to coerce an object? Why would you do it?  
A: To coerce the object into an expected type. You might do this in order to try and force an unknown object type into the expected type or format required by the operation.

Q: What is the difference between a statement and an expression in Ruby?  
A: All statements are expressions in Ruby since all statements return a value. A statement is simply a way to refer to a certain type of syntax.

Q: What module would need to use for cryptographically secure random numbers?  
A: `SecureRandom`

Data Types
-------------------------------------------------------------------------------

### String

Q: Are strings mutable?  
A: Yes.

Q: What is the output of the expression `"hello"[-1]` ?  
A: `"o"`

Q: What does `String#chomp` do?  
A: Removes a line terminator.

Q: What does `String#chop` do?  
A: Removes the trailing character or line terminator.

Q: Why might you want to avoid using string literals within loops?  
A: A new object is created for every string literal even when the values are identical.

Q: Is a `String` object enumerable in Ruby 1.9+?  
A: No.

Q: What method might you use to enumerate over a `String` in Ruby 1.9+?  
A: `#each_char`

Q: What is the difference between a character literal such as `?A` and a string literal such as `"A"`?  
A: There is no difference in Ruby 1.9+.

### Symbol

Q: What is a symbol?  
A: Symbols are scalar value objects used as identifiers, mapping immutable strings to fixed internal values.

Q: Why are symbols typically used as hash keys instead of strings?  
A: Strings are mutable while symbols are immutable. Though Ruby internally makes an immutable copy of a string when used as a hash key, comparing two symbols is faster than comparing two `String` objects. This is also a convention.

Q: What can't you do to instantiations of `Symbol` and `Fixnum` that you can do to all other instances of core Ruby objects?  
A: Define singleton methods on them.

### Numeric

Q: Are `Numeric` objects mutable?  
A: No.

Q: Symbols are mutable objects. Name another immutable core Ruby object.  
A: `Fixnum`

Q: What happens when a value is too big for `Fixnum`?  
A: It is automatically converteed to a `Bignum`.

Q: The superclass of `Fixnum` is _\_\_.  
A: `Integer`

Q: The superclass of `Integer` is _\_\_.  
A: `Numeric`

Q: What numeric class might you use to avoid the rounding error inherent in the use of binary floating-point arithmetic?  
A: `BigDecimal`

### Array

Q: What method might you use to remove duplicate values from an array?  
A: `#uniq`

### Hash

Q: Name one synonym for `#key?`?  
A: `#has_key?`, `#include?`, `#member?`

Q: How do you specify a default value for a hash?  
A: Pass the default values as an argument to `#new` on initialization or change the default directly with the setter method `Hash#default`. You may also provide a default at time of query using `#fetch`.

Q: Does `Hash` use `#==` or `#eql?` to compare hash keys?  
A: `#eql?`

Q: In what order are the values of a hash iteration in Ruby 1.9+?  
A: The order in which they were inserted.

Q: What is the synonym of `Hash#store`?  
A: `Hash#[]=`

Q: Why can you safely use a `String` as a hash key, even though a string is a mutable object?  
A: Because Ruby makes a private copy of a string used as a hash key.

Q: Why might you want to use `Hash#fetch` over `Hash#[]` when querying values in a hash?  
A: It provides options for handling the case where a key does not exist in the hash.

Q: When would you need to use `Hash#rehash`?  
A: After you mutate a mutable hash key.

### Range

Q: What are two uses of ranges?  
A: comparison, iteration

### Regexp

Q: What is the regular expression modifier to ignore case?  
A: `i`

Q: What is the pattern matching operator?  
A: `#~=`

Q: How might you include an expression within a `Regexp` literal?  
A: Using `#{}` just like as in a double-quoted string literal.

Q: What is the global variable for the last `Regexp` match?  
A: `$LAST_MATCH_INFO` equivalent to `$~`

Operators
-------------------------------------------------------------------------------

Q: What are two uses of the splat operator?  
A: Explode/expand the elements of an array. Collect arguments of a parameter list into an array.

Q: What is the only operator that operates on three operands?  
A: The conditional operator `?:` (sometimes referred to as the ternary if operator).

Q: Which operator must be defined in order to implement the `Comparable` module?  
A: `<=>`

Q: What is the difference between `#==` and `#equal?`?  
A: `#==` performs the generic comparison and is implemented differently across classes while `#equal?` is defined on `BasicObject` and compares object identity. Therefore, `#equal?` should not be overridden in subclasses.

Q: What is the difference between `#==` and `#===`?  
A: `#==` performs the generic comparison while `#===` performs case equality comparison and is useful for providing meaningful semantics in case statements.

Q: What is the difference between `#==` and `#eql?`?  
A: `#eql?` is sometimes an alternate equality. `Hash` uses `#eql?` to test for hash key equality. `Numeric` types perform type conversion across `#==` but not across `#eql?`, thus `#eql?` performs a stricter comparison than `#==` in that case.

Q: Which binds more tightly? `&&` or `and`  
A: `&&`

Q: Which binds more tightly? `&&` or `=`  
A: `&&`

Q: Which binds more tightly? `and` or `=`  
A: `and`

Q: Which binds more tightly? `&&` or `||`  
A: `&&`

Q: What is the arity of an operator?  
A: The number of values the operator performs on.

Control Structures
-------------------------------------------------------------------------------

Q: What is a statement modifier?  
A: A condition after a statement such as with `x = 1 if a == true`

Q: Does a while block define it's own variable scope?  
A: No.

Q: Does a case statement have fall-through behavior?  
A: No.

Q: What is the difference between `throw/catch` and `raise/rescue`?  
A: `throw` and `catch` accept matching symbols as arguments and should be considered a control-flow structure where `raise` and `rescue` is used to raise and handle exceptions. `throw` and `catch` are not commonly used while exception handling with `raise` and `rescue` is used often - a `rescue` clause is a fundamental part of the Ruby language.

Q: Does a `rescue` block define it's own variable scope?  
A: No.

Q: What are some advantages of a case statement versus repeated `elsif` statements?  
A: It shows intent. It DRY's out the condition.

Q: What are some disadvantages of a case statement versus repeated `elsif` statements?  
A: The statement is typically resistant to modification without a complete refactoring of the entire control structure. The case statement can be confusing if multiple comma-separated expressions are associated with a single when clause.

Blocks and Iterators
-------------------------------------------------------------------------------

Q: Name three methods of the `Enumerable` module.  
A: `#each`, `#map`, `#select`, `#find`, `#inject`...

Q: Name two `Enumerable` classes (classes which mix in the `Enumerable` module).  
A: `Array`, `Hash`, `Set`, `Range`, `IO`...

Q: When might you use the `do`/`end` syntax versus using the curly bracket syntax for a block?  
A: The `do`/`end` syntax for a block is commonly used for multiline statements. An alternate convention is to use curly bracket syntax for blocks that return a value while using `do`/`end` syntax for blocks that change the state of the system somehow and do not return a value.

Q: What is an iterator?  
A: An object that allows traversal of the elements of the container. In Ruby, an iterator is any method that uses the yield statement.

Q: How do you define block-local variables in a block's parameter list?  
A: Variables that appear after a semicolon in a block's parameter list are guaranteed to be local to the block.

Q: What is the synonym of `#include?`?  
A: `#member?`

Q: Can a collection be modified while it is being iterated upon?  
A: Yes.

Q: Is a block an object?  
A: No. A block is a syntactic structure of the interpreter. However, a block can be converted to a Proc object.

Q: What is the synonym of `#collect`?  
A: `#map`

Q: What is the synonym of `#find`?  
A: `#detect`

Q: What is the synonym of `#select`?  
A: `#find_all`

Q: What is the opposite of `#select`?  
A: `#reject`

Q: What is the synonym of `#inject`?  
A: `#reduce`

Q: Why might you use `#each` instead of `for/in`?  
A: It's the "Ruby way" - it is an example of how Ruby defines methods that mimic natural language concepts. Iterator methods such as `#each` read more naturally. `#each` is a block so it defines a new variable scope. `for/in` depends on the existence of `#each` which implies that `#each` is a more fundamental part of the language.

Q: What happens if a bock in Ruby 1.9+ is passed two arguments but only accepts one argument?  
A: Nothing. Only the first argument will be passed to the block.

Q: How is a block anonymous?  
A: It doesn't have a name. It doesn't exist beyond it's execution unless converted to a Proc object.

Q: How does block invocation differ from method invocation?  
A: Ruby will throw an exception if more than the expected number of arguments are passed to a method. A block will simply ignore the extra values in Ruby 1.9+.

Methods
-------------------------------------------------------------------------------

Q: Can methods be overloaded?  
A: No.

Q: How would you test whether an object has a method?  
A: `#respond_to?` or `#method?`

Q: What is `self`?  
A: The current object.

Q: What does a bang `!` at the end of a method signify?  
A: That it should be used cautiously. Methods with this naming convention typically perform a mutation on the receiver object.

Q: What is a mutator method?  
A: A method which alters the internal state of the object receiver.

Q: Is a method an object?  
A: No, however, a `MethodObject` is an object.

Q: What is a predicate in the context of Ruby method naming conventions?  
A: A method that answers a question posed by the method invocation or method name. Predicates typically return a boolean.

Q: Are instance methods public or private?  
A: They are public by default. You can change their visibility using `Module#private`, `Module#protected`, or back again using `Module#public`.

Q: When might you explicitly use the `return` statement.  
A: To return from a method prematurely or to return multiple values.

Q: Why might you want to alias a method?  
A: To create a synonym for the method that is more readable or appropriate for the context of some problems. To add functionality to a method.

Q: How might you send a message to a private method of a receiver object from outside the scope of the receiver object?  
A: `#send`

Q: How might you prevent future modifications to an object?  
A: `#freeze`

Q: How is the invocation of a private method different than the invocation of a public method from within its defining class?  
A: It must be referenced in a functional manner without an explicit receiver object and not on the class object itself or on the current object `self`.

Q: Can method names be capitalized?  
A: Yes, but the convention is that they are not.

Q: What is the difference between private and protected methods?  
A: A private method can only be called by any instance methods of the defining class or any subclasses and must be invoked in a functional style and not explicitly on `self` such as with `self.my_method`. A protected method may be explicitly invoked by any instance of the defining class, and is not restricted to implicit invocation on `self`.

Q: What is a singleton method?  
A: A method that is available only on a single object.

Q: What is method name resolution?  
A: The runtime lookup of the appropriate definition of a method.

Q: How does `return` differ from within a method than from within a block?  
A: `return` within a method returns from the method. `return` within a block returns from its lexically enclosing method.

Q: Are class methods public or private?  
A: They are public by default. You can change their visibility using `#private_class_method` and back again using `#public_class_method`.

Q: Does a method return a value if it does not contain an expression?  
A: Yes, it returns `nil`.

Q: Name one instance when parenthesis are required in method invocation?  
A: In the case of nested method invocation such as `f(g())`.

Q: If a method is declared outside a class or module definition at the top-level, where does it live?  
A: As a private instance method of `Object`, whose value of `self` resolves to the special "main" object.

Q: What is the origin of the "keywords" `public`, `private`, and `protected`?  
A: They are instance methods of the `Module` class. Since `Class` subclasses `Module`, the methods can be invoked without explicit reference to `self` such as `self.private`.

Q: Describe the method name resolution process.  
A:  
1. Check eigenclass for singleton methods including inheritance of eigenclasses on class objects.  
2. Check for instance methods.  
3. Check for instance methods of any included modules.  
4. Check instance methods and instance methods of any included modules in the inheritance hierarchy.  
5. Invoke `#method_missing` following steps 1-4, resolving to `Kernel#method_missing` if not found.

Q: How do you define a private class method?  
A: Define the class method and then call `#private_class_method` with an argument as a symbol of the class method name.

Q: Name two ways to disable methods.  
A: `undef method_name`, `#remove_method`, `#undef_method`

Q: What is the difference between `#remove_method` and `#undef_method`?  
A: `#undef_method` prevents any invocation of the method through an instance of the class, while `#remove_method` will remove the method definition from the class, but not prevent inherited methods of the same name from being invoked.

Q: Explain how Ruby syntax supports object specifiers in parameters lists?  
A: You can leave off the curly brackets from a hash in a parameter list, assuming it is the only argument in the list.

Procs and Lambdas
-------------------------------------------------------------------------------

Q: What are the two varieties of Proc objects?  
A: Procs and lambdas.

Q: How do you accept an associated block within a Proc's paramters list.  
A: Prefix `&` to the last parameter.

Q: What is true about a method argument that is prefixed with `&`?  
A: It will refer to the calling block as a named Proc object. It must be the last argument in the parameter list.

Q: What is the main difference between procs and lambdas?  
A: Calling a lambda is more akin to invoking a method where a return statement in a lambda will return from the lambda itself, instead of returning from the lexically enclosing method, as procs do. Adding to this notion, lambdas must be invoked with the exact number of arguments as is required by method invocation, whereas procs are more flexible in receiving arguments.

Q: Does an object have to be a Proc object for a `&` to be prefixed to it in a parameter list?  
A: No, `&` can appear before any object with a `#to_proc` method.

Q: What is the difference between a Proc invocation and a lambda invocaton?  
A: There must be a block associated with lambda invocation. Lambdas must be invoked with the exact number of arguments as is required by method invocation, whereas procs are more flexible in receiving arguments.

Q: When might you encounter a `LocalJumpError`?  
A: You would encounter this exception when attempting to return from a method that has already returned such as if you attempt to return from a Proc object whose lexically enclosing method has already returned.

Closures
-------------------------------------------------------------------------------

Q: What is a closure?  
A: A closure is an object that is both an invocable function together with a variable binding. The object retains access to the local variables that were in scope at the time of the object definition.

Q: Does a closure in Ruby retain variables by value or by reference?  
A: By reference; the closure also extends the lifetimes of its variables.

Q: A closure's reference to its variables is said to by dynamically bound. What does this mean?  
A: The values of the variables are looked up when the Proc object is executed.

Q: Is it possible to alter a closure?  
A: Yes, you can access and alter the binding of a closure with `#binding`.

Method Objects
-------------------------------------------------------------------------------

Q: What must you do first before you can invoke an `UnboundMethod` object?  
A: Bind it to a receiver object using `#bind`.

Q: Are method objects closures?  
A: No.

Q: How do you obtain a `Method` object from an existing module/class?  
A: Using `Object#method`

Q: How do you obtain an `UnboundMethod` object from an existing module/class?  
A: Using `Module#instance_method`

Constants
-------------------------------------------------------------------------------

Q: Are constants public or private?  
A: Public.

Q: What happens if you attempt to define a constant on a class from outside the class?  
A: It defines it successfully since constants are publicly accessible and assignable.

Q: What happens to a constant that is not assigned?  
A: It does not exist.

Q: If there exists `A::CONSTANT`, and `B` is a subclass of `A`, what does a reference to `CONSTANT` (without a scope resolution operator) resolve to within the lexical scope of `B`?  
A: `B::CONSTANT` since `B` has inherited `A::CONSTANT`.

Q: What is wrong with the following code?  
```ruby
class MyClass
  def my_method
    MY_CONSTANT = "hello"
  end
end
```

A: A constant cannot be assigned within the body of a method. Dynamic constant assignment is not allowed.

Classes
-------------------------------------------------------------------------------

Q: What does `#attr_accessor` do?  
A: Creates getter and setter methods for all the symbols naming attributes it is passed as arguments.

Q: What is the difference between an instance variable and a class variable?  
A: A class variable is always evaluated in reference to the class object created by the enclosing class definition while an instance variables is always evaluated in reference to `self`. Instance variables cannot be used outside of instance methods.

Q: Why must a class name begin with a capital letter?  
A: Because the class keyword creates a new constant that refers to the class and constants must begin with a capital letter.

Q: Is `#initialize` an instance method or a class method?  
A: An instance method.

Q: Why can't a class instance variable be used within an instance method?  
A: Because it would be an instance method.

Q: What is the difference between a class variable and a class instance variable?  
A: Class instance variables are instance variables of a class. Class instance variables cannot be used within instance methods.

Q: What is a singleton?  
A: A class with only one instance.

Q: What is the difference between a singleton and a singleton method?  
A: A singleton is a class with only one instance while a singleton method is a method that is available only on a single object.

Q: How do you create a singleton?  
A: By including the `Singleton` module.

Q: Can you defined accessor methods for class instance variables?  
A: Yes, if they are defined as singleton methods of the class.

Q: Can classes be nested?  
A: Yes.

Q: Is `#initialize` public or private?  
A: Private by default.

Q: What does `#allocate` do?  
A: Creates an uninitialized instance of a class.

Q: What is an eigenclass?  
A: An anonymous class associated with an object. An object's singleton methods are instance methods of its associated eigenclass.

Q: What is the relationship between singleton methods and class methods?  
A: Class methods are singleton methods of the eigenclass associated with the class object.

Q: What is `Class::new`?  
A: A class method of the `Class` object that creates new classes.

Q: If `Class` `B` is nested within `Class` `A`, and there exists a class method on `A`, does `Class` `B` have access to this instance method on `Class` `A`?  
A: No. Nesting one class within another does not give the inner class any special access to the methods or variables of the outer class.

Q: Are eigenclasses inherited?  
A: The eigenclasses of an object are inherited from the eigenclasses of the superclass of the class object. An eigenclass of an object instance stands alone and does not inherit from any other classes.

Q: What happens to any return value of `#initialize`?  
A: It is ignored.

Q: What is a factory method?  
A: An initialization method that creates specialized instances of a class.

Q: What is the method to run initialization code on copied instances of an object?  
A: `#initialize_copy`

Q: What object is passed to `#initialize_copy`?  
A: The original object that is being copied.

Q: Does `#initialize_copy` override `#initialize`?  
A: No.

Q: What does it mean that `#dup` and `#clone` perform shallow copies?  
A: The instance variables of the copy are copied by reference rather than by value.

Q: What is the difference between `#dup` and `#clone`?  
A: `#clone` copies the frozen state of an object and any singleton methods of an object while `#dup` does neither.

Q: Why might you not need to pass any arguments to the `#initialize` method of a singleton class?  
A: Since there is only one instance of the class, there will only be one variation of the instance so any values it contains may be set explicitly from within the class definition (such as in the `#initialize` method itself).

Modules
-------------------------------------------------------------------------------

Q: What are the two functions of modules?  
A: As mixins or as namespaces.

Q: Can a module be subclassed?  
A: No.

Q: What happens when a class includes a module?  
A: The instance methods of the module become instance methods of the class.

Q: What happens when an object extends a module?  
A: The instance methods of the module become singleton methods on the object.

Q: What is the superclass of `Class`?  
A: `Module`

Q: Why must module names begin with a capital letter?  
A: Because the module keyword creates a new constant that refers to the module and constants must begin with a capital letter.

Q: How might you check if a module has been included by an object?  
A: Using `#is_a?` such as with `my_obj.is_a? MyModule`.

Q: Concerning those methods that are namespaced by a module, why might you explicitly invoke those methods on `self` rather than on the name of the module?  
A: To DRY up the code. If the name of the module were to change then you would not have to change all the references to that module name. The object referenced by `self` would not change.

Q: Inferring from the behavior of `Module#include`, is this method a public or private instance method of `Module`?
A: Private, because it can't be used outside of a `Module` or `Class` definition.

Q: What does `#module_function` do?  
A: Makes class copies of the specified methods and makes instance methods private.

Structs
-------------------------------------------------------------------------------

Q: What is a `Struct` in Ruby?  
A: A core Ruby class that generates other classes containing accessor methods for the specified fields.

Q: Can you add methods to a `Struct`?  
A: Yes.

Inheritance
-------------------------------------------------------------------------------

Q: What's the difference between `#is_a?` and `#instance_of?`?  
A: `#instance_of?` ignores inheritance and any mixed-in modules.

Q: If `#super` is invoked without any arguments, which if any arguments get passed to the superclass method?  
A: All the arguments that were passed to the subclass method will be passed to the superclass method.

Q: Are instance methods inherited?  
A: No, since they are not defined by a class and thus are unrelated to the inheritance mechanism.

Q: Are class methods inherited?  
A: Yes.

Q: Are constants inherited?  
A: Yes.

Q: Are class variables inherited?  
A: No. The behavior is different than inheritance. Any alteration of a class variable by a subclass affects that class variable in the superclass and all other subclasses of the superclass.

Q: Why might you not want to use class variables?  
A: Their values can be changed at any point in the inheritance chain which could cause unexpected behavior in parent classes or subclasses which use those class variables.

Q: What should you look out for when subclassing a class that is unknown to you?  
A: Overriding private methods or overwriting class variables.

Q: How might you prevent a method on a superclass from being inherited by a subclass?  
A: Override the method on the subclass or `undef` the method in the subclass.

Metaprogramming
-------------------------------------------------------------------------------

Q: Name one method in Ruby core that might be considered "metaprogramming."  
A: `#attr_reader`, `#attr_accessor`, `#define_method`, `#method_missing`, `#const_missing`, `#eval`, `#class_eval`, `#instance_eval`...

Q: Is `#attr_reader` an example of metaprogramming?  
A: Yes, since it creates getter methods at the time of the enclosing class definition.

Q: How might you access an instance variable of a receiver object from outside the scope of the receiver object?  
A: With an accessor method or using `#instance_variables_get`, `#instance_eval`, or `binding.eval`.

Q: Which method is invoked when a method is not found?  
A: `#method_missing`

Q: How do you open an eigenclass from within its associated class?  
A: `class << self`

Q: Why should you avoid calling `#eval` on text received from a user?  
A: Because it could be malicious.

Q: What is a binding?  
A: A representation of an object's variable bindings at some moment.

Q: What is Ruby's reflection API?  
A: A collection of methods mostly defined by `Kernel`, `Object`, and `Module` that allow a program to examine its own state and structure.

Q: Which method is called when a constant is not found?  
A: `#const_missing`

Q: `#define_method` accepts how many and of what types of arguments?  
A: A symbol as the method name and either a block or a `Method` object as the method body.

Q: Does `#eval` accept a block?  
A: No, `#eval` can only accept a string. `#class_eval` and `#instance_eval` accept blocks.

Q: How might you obtain a reference to an eigenclass from within its associated class?  
A: `eigenclass = class << self; self; end`

Q: How might you change method visibility from outside a class definition?  
A: Using `#class_eval`

Q: Why is `#eval` useful for testing code?  
A: Because it doesn't alter the local scope.

Q: What is the difference between `#instance_eval` and `#instance_exec`?  
A: `#instance_exec` can only accept a block, and not a string, and it can accept arguments and pass them to the block, allowing the block to be evaluated in the context of the receiver object with parameters whose values come from the block.

Q: Where do `#class_variable_get` and `#class_variables_set` live in the object model?  
A: `Module`

Q: Where do `#instance_variable_get` and `#instance_variables_set` live in the object model?  
A: `Object`

Q: Where do `#local_variables` and `#global` live in the object model?  
A: `Kernel`

Loading Modules, Files, and Gems
-------------------------------------------------------------------------------

### Loading

Q: Which is more common, `#require` or `#load`?  
A: `#require`

Q: What is `$LOAD_PATH`?  
A: A global array of strings of the directories to be searched when loading files with the load and require methods. `$LOAD_PATH` is equivalent to `$:`.

Q: What is the difference between `#require` and `#load`?  
A: `#require` can load binary extensions. `#require` does not require a filename extension. `#require` prevents multiple loads of the same file path. `#load` loads the specified file at the current `$SAFE` level while `#require` loads the specified file with a `$SAFE` level of 0.

Q: Does a file loaded with `#require` or `#load` have access to the local variables of the loading file?  
A: No.

Q: What is the difference between `#require` and `#require_relative`?  
A: `#require_relative` ignores the load path.

Q: What does `#autoload` do?  
A: Allows lazy-loading of files when a constant assigned to a file is first referenced.

### Files

Q: What does `File#expand_path` do?  
A: Converts a relative path to a fully qualified path.

Q: What method in `Dir` is used to list the contents of a directory?  
A: `#entries` or `#foreach`

Q: What is an `IO` object?  
A: An IO object is an instance of class IO that can be used for reading or writing binary data to and from a file.

### Gems

Q: In Ruby 1.9+, are RubyGems installation directories included in `$LOAD_PATH`?  
A: Yes.

Q: In Ruby 1.9+, if more than one version of a Gem is installed, which version will be used?  
A: The Gem with the highest version number.

Q: In Ruby 1.9+, how would you alter the default version of a Gem that will be used?
A: Using `Kernel#gem`.

Security
-------------------------------------------------------------------------------

Q: What can you say about objects derived from tainted objects?  
A: They will also be tainted.

Q: What is the default `$SAFE` level?  
A: 0

Q: What happens when you attempt to lower the `$SAFE` level?  
A: You cannot lower the `$SAFE` level. It can only be raised.

Q: What is the difference between taint and trust?  
A: Taint is derived from the environment such as the command line, environment variables, files, sockets, etc..., while trust is derived from the `$SAFE` level of the originating code. Untrusted objects are both untrusted and tainted.

Exceptions
-------------------------------------------------------------------------------

Q: What error is raised if a method is passed the wrong number of arguments?  
A: `ArgumentError`

Q: What error is raised if no `#method_missing` methods resolve to a method?  
A: `NoMethodError`

Q: The superclass of `StandardError` is _\_\_.  
A: `Exception`

Q: What does the default implementation of `Kernel#module_missing` do?  
A: Just raises a `NoMethodError`.

Q: What happens if you attempt to redefine `BasicObject#__send__`?  
A: Ruby issues a warning.

Debugging
-------------------------------------------------------------------------------

Q: What is the difference between `#to_s` and `#inspect`?  
A: `#inspect` is the same as `#to_s`, except for that some classes redefine `#inspect` to provide output that is more helpful in debugging.

Q: What is the difference between `#puts` and `#p`?  
A: `#p` converts objects to strings with the `#inspect` method instead of with `#to_s`.

Q: Which Ruby interpreter option enables debugging?  
A: `-d` or `--debug`

Q: What is the global variable for the last exception raised?  
A: `$ERROR_INFO` equivalent to `$!`

Q: How might you obtain the current state of the call stack?  
A: Using `Exception.backtrace` or `Kernel#caller`

Q: What does `Kernel#__method__` return?  
A: The name as a symbol of the currently executing method.

Q: In Ruby 1.9+, what is the synonym of `Kernel#__method__`?  
A: `Kernel#__callee__`

The Ruby Environment and the Interpreter
-------------------------------------------------------------------------------

Q: What does MRI most commonly stand for?  
A: Matz's Ruby Interpreter

Q: What does IRB stand for?  
A: Interactive Ruby

Q: What is the difference between `#puts` and `#prints`?  
A: `#puts` appends a newline to the output.

Q: Where do the curly brackets to define a hash literal `{}` exist in Ruby's object model?  
A: It does not exist within the object model. It exists as a function of the interpreter.

Q: What is the default encoding in MRI?  
A: ASCII

Q: What is the global constant used to access environment variable settings in effect for the interpreter?  
A: `ENV`

Q: How does Ruby know that a setter method such as `X#[]=` will be called in the expression `x = X.new; x.field = []`?  
A: It is a syntactical conversion of the interpreter.

Q: What is the global constant to access arguments specified on the command line?  
A: `ARGV`

Q: Which Ruby interpreter option enables warning about deprecated or problematic code?  
A: `-w`

Q: In MRI, which objects are not subject to garbage collection?  
A: Symbols.

Q: What module in the standard library enables English language alternatives to terse global variables?  
A: `English`

License
===============================================================================

The textual contents of this document are licensed in the manner specified in the accompanying LICENSE file in order to ensure that this work and all contributions remain open.

Ruby logo is Copyright (c) 2006, Yukihiro Matsumoto, used under [Creative Commons](http://en.wikipedia.org/wiki/Creative_Commons) [Attribution-Share Alike 2.5 Generic](http://creativecommons.org/licenses/by-sa/2.5/deed.en) license. Use of the logo here does not suggest that this work is endorsed by Yukihiro Matsumoto or the Ruby Visual Identity Team.
