Ruby
====

Use Rbenv or RVM version/environment managers

#### Usage

	$ ruby -v   # version of ruby installed
	$ irb       # ruby interpreter 


#### Types

	$ a.class   # returns type of variable (string, fixnum etc)

#### Strings

Variable Interpolation

	puts "Hello #{name}"   # variable interpolated
	puts 'Hello #{name}'   # variable not interpoloated

String Methods

[Ruby String Methods Docs](http://ruby-doc.org/core-2.2.0/String.html)

	a.upcase          # makes string uppercase
	a.downcase        # makes string lowercase
	a.reverse         # reverses characters in string
	a.upcase.reverse  # uppercases and reverses string

Replacement

``` ruby

a = "test"
b = "failed"

puts "I totally #{b} the #{a}!"

```

User Input

``` ruby

print "Enter your Name"
name = gets
puts "Hello #{name}"

```

New line characters & whitespace

	\n   # newline
	\t   # tab
	\s   # space

#### Methods

``` ruby

# This is a comment in ruby

def add(a, b)

	return a + b

end


```

Load Methods

	$ irb
	irb(main)> load "./test.rb"
	irb(main)> sum = add(100+100)






