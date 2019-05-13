## CheatSheet.md

### Core syntax: 
`object.method` or `object.method(args)` for methods that need arguments.

Syntax for creating a new variable of a Class and storing them in a varible:  
`var = my_class.new`

**.class method:**  
Returns the class of the object.  
`"Hello".class # => String`  
`2.class # => Integer`  
`2.3.class # => Float`
`var.class # => my_class`

#### Exceptions:
There are a few methods that do not follow the core syntax.

**p (print):**  
Prints the arguments following it.  
`p "Hello!" # => "Hello!"`  

**puts (put string):**  
Similar to `p`, but the quotes around strings are removed.  
`puts "Hello!" # => Hello!`  

**gets (get string):**  
Will pause the program and wait for the user to type something in the terminal and press return. Returns a String with the user's input.

**rand:**  
Returns a random integer within a range when given an Integer as an argument.  
`rand(3) # returns a whole number between 0 and 2`  
Returns a random integer between the lower limit and the upper limit when given a Range as an argument.  
`rand(1..10) # returns a whole number between 1 and 10, including 1 and 10`
Returns a random decimal between 0 and 1 when not given any argument.  
`rand # returns a decimal between 0 and 1`  

***Note:***  
With Ruby `Range`s, two dots means inclusive of the second value, and three dots means exclusive of the second value. E.g., `(1..4)` is 1, 2, 3, and 4; `(1...4)` is only 1, 2, and 3.

### Class String

**.concat (.+ / +) method:**  
Appends the given arguments to a string. when given an integer as an argument, it converts the integer into ASCII code.  
`"hi".concat(33)`
> "hi!"   

`"Rub".concat(121)`  
>"Ruby"

When given a string literal as an argument, it adds that string to the original string. `.+` or `+` is shorthand for `.concat` method. Each line of code below will give the same output.  
`"hi".concat(" there")`  
`"hi".+(" there")`  
`"hi" +(" there")`  
`"hi" + " there"`  
> "hi there!"

`.+` or `+` will throw an error when passed an integer because the ruby interpreter thinks you are trying to add string to an integer.  
`"hi".+(33)`  
`"hi" + 33`
> ERROR!


**\* method:**  
Multiplies the original string by the given integer.  
`"Ya" * 5`
> "YaYaYaYaYa"

`"Ya" * 0`
> ""

**.upcase method:**  
Converts all lowercase letters to their uppercase counterparts in the given string.  
`"hello".upcase`
> "HELLO"

**.downcase method:**  
Converts all the uppercase letters to their lowercase counterparts in the given string.  
`"HI".downcase`
> "hi"

**.swapcase method:**  
Converts all the uppercase letters to their lowercase counterparts and lowercase letters to their uppercase counterparts in the given string.  
`"Hi There".swapcase`
> "hI tHERE"

`"hI tHERE".swapcase`
> "Hi There"

**.reverse method:**     
Returns a new String with the characters from the original String in reverse order.  
`"stressed".reverse`  
> "desserts"  

**.length method:**  
Returns the character length in a String as an integer.  
 `"hippopotamus".length`
> 12


**.chomp method:**  
When not given any argument, removes the "\n" (newline) character from the end of the string. When given an argument of a charcter or a string, it remove that argument from the *end* of the orginal string.  
`"Hey!\n".chomp`  
`"Hey!".chomp("!")`  
`"Hey There".chomp("There")`  
`"Hey!".chomp("y")`
>"Hey!"  
>"Hey"  
>"Hey "  
>"Hey!"

```
p "What is your name?"
name = gets # supposes the user inputs "Clark" and then hits return
p "Hi" + name
```
>"Hi Clark\n"  

```
p "What is your name?"
name = gets # supposes the user inputs "Clark" and then hits return
p "Hi" + name.chomp
```
>"Hi Clark"

```
p "What is your name?"
name = gets.chomp # supposes the user inputs "Clark" and then hits return
p "Hi" + name
```
>"Hi Clark"

**.gsub method:**  
Substitutes the all occurances of the first argument with the second argument in original string.  
`"Hello".gsub("ello", "i")`
>"Hi"  

`"Hi.there".gsub(".", " ")`  
>"Hi there"  

Giving an empty string as the second arugment deletes any occurences of the first arugument in the string.   
`"example @ ruby.com".gsub(" ", "")`  
>"example@ruby.com" 

**.to_i method:**  
Converts a string literal that contains a number to an integer.  
`"8".to_i`
>8

```
p "What is your lucky number?"
lucky_number = gets.chomp # Suppose the user types is "7" and then hits return
square = lucky_number ** 2 # This will throw an error.
```
>NoMethodError (undefined method '**' for "7":String)

This is where the `.to_s` method comes handy.
```
p "What is your lucky number?"
lucky_number = gets.chomp # Suppose the user types is "7" and then hits return
square = lucky_numbe.to_i ** 2 # This will throw an error.
p square
```
>"49"

**.strip method:**  
Removes all leading and trailing whitespace in the string.  
`"   hi there ".strip`
>"hi there"

**.capitalize method:**  
Capitalizes the first character of a string.  
`"capitalize".capitalize`
>"Capitalize"

**.split method:**  
Splits a string into an substrings and creates an Array of these substrings. when not given argument, `.split` uses whitespace to divide the string. when given an argument, `.split` divides the string on that argument.  
`"Hello hi byebye".split`
>["Hello", "hi", "byebye"]

`"one!two!three!".split("!")`
>["one", "two", "three"]`

### Class Integer
whole numbers

**Math Operations for the Integer Class:**   
`12 + 5 # => 17`  
`12 - 5 # => 7 `  
`12 * 5 # => 60`  
`12 / 5 # => 2`  
The `/` operator for integers only returns a whole number and omits the remainder.

`%` **(modulus) operator:**  
Returns the remainder from a divisions.  
`13 / 5 # => 3`

`**` **operator:**  
Raises a number to a power.  
`3 ** 2 # => 9`  
`2 ** 3 # => 8`

**.odd? and .even? methods:**  
Returns a *boolean* based on whether the integer is odd or even.  
`7.odd?`
>true

`8.odd?`
>false

`8.even?`
>false

`7.even?`
>false

**.to_s method:**  
Converts an integer to a string literal.  
`8.to_s`
>"8"

```
lucky_number = rand(10) # assigns a random integer between 0 to 9 to the variable lucky_number
p "My lucky number is " + lucky_number + "!" 
```
The above block of code won't work and will throw an error. 
>**TypeError (no implicit conversion of Integer into String)**

This is where the `.to_s` method comes handy. 
```
lucky_number = rand(10) # assigns a random integer between 0 to 9 to the variable lucky_number
p "My lucky number is " + lucky_number.to_i + "!" 
```
>"My lucky number is 7!"

`"There are " + 7.to_s + " pineapples."`
>"There are 7 pineapples"

**.to_f method:**  
converts an integer to a float(decimal).  
`7.to_f`
>7.0

### Class Float
decimals

**Math Operations for the Float Class:**  
Standard operations are similar to those for the Integer class. The only exception is the `/` operator which returns fractional results.  
`12 / 5 # => 2`  
`12.0 / 5.0 # => 2.4`  
`12 / 5.0 # => 2.4`  
`12.0 / 5 # => 2.4`  

`**` **operator:**  
The `**`operator for Floats can additionally be used to calculate roots.  
`9 ** 0.5 # => 3.0, since 9^(1/2) = sqaureroot of 9`  
`8 ** (1/3.0)# => 2.0, since 8^(1/3) = cuberoot of 8`  

**.round method:**  
Returns the whole part of a decimal when not given any argument.  
`3.14159.round # => 3`  
When given an argument, returns a decimal rounded to the number of decimal places specified by the argument.  
`3.14159.round(3) # => 3.142`  
`3.14139.round(3) # => 3.141`  

**.to_i method:**  
Converts a float to an integer by rounding the float down to closest whole number.  
`"8.9".to_i`  
>8

`"8.1".to_i`  
>8

#### Integer and Float division examples
`12 / 5 # => 2`  
`(12 / 5).to_f # => 2.0`  
`12.to_f / 5 # => 2.4`  
`12 / 5.to_f # => 2.4`  
`(12.0 / 5 ).to_i # => 2`  
`(12 / 5.0).to_i # => 2`  

### Class Date

**Creating a Date:**  
To use the Date class in a Ruby program, we need to say:  
`require "date"`  
***Note:***
Only *Ruby* programs need to have a `require` statement for the Date class. *Rails* already does this for you.

**Date.new**  
Use the `.new` method to create a new instance of a Date object. The `.new` method can be used with or without argument. When given no arguments, the default date is set to *Jan 1st, -4712 BCE*.
```
Date.new                  # => #<Date: -4712-01-01 ((0j,0s,0n),+0s,2299161j)>
Date.new(2001)            # => #<Date: 2001-01-01 ...>
Date.new(2001,2,3)        # => #<Date: 2001-02-03 ...>
Date.new(2001,2,-1)       # => #<Date: 2001-02-28 ...>
```
**Date.today**  
Initializes a Date object to the current date.   
`Date.today # => #<Date: 2019-04-16 ((2458590j,0s,0n),+0s,2299161j)>`  

**Date.parse()**  
Returns an Date object initialized to a date, interpreted from the given String argument.
```
Date.parse("2001-02-03") # => #<Date: 2001-02-03 ...>
Date.parse("20010203") # => #<Date: 2001-02-03 ...>
Date.parse("3rd Feb 2001") # => #<Date: 2001-02-03 ...>
```

**Subtraction**  
Two dates can be subtracted from one another. The `-` operator returns a Rational which can be converted into an Integer to find the days in between the two dates.  
```
number_of_days = Date.today - Date.parse("July 4, 1776") 
# => number_of_days = (88674/1)
number_of_days.to_i # => 88674
```

**Date.mday**  
Returns the day of the month (1-31).
```
held_on = Date.new(2001,2,3)
held_on.mday # => 3
```

**Date.wday**  
Returns the day of the week (0-6, Sunday is 0).
```
held_on = Date.new(2001,2,3)
held_on.wday # => 6
```
**Days of the Week**  
```
date = Date.new
date.monday? # => true if date is a Monday.
date.tuesday? # => true if date is a Tuesday.
date.wednesday? # => true if date is a Wednesday.
date.thursday? # => true if date is a Thursday.
date.friday? # => true if date is a Friday.
date.saturday? # => true if date is a Saturday.
date.sunday? # => true if date is a Sunday.
```

### Class Array

list of objects represented with square brackets, [].


**Creating an Array:**  
`.new` initializes a new empty Array.  
`cities = Array.new # => cities = []`  
or  
`cities = [] # => cities = []` 

**.push method:**  
Adds elements to an Array. 
```
cities.push("Chicago")
cities.push("Los Angeles")
cities.push("New York City")
```
or  
`cities = ["Chicago", "Los Angeles", "New York City"] # Initializes and adds elements to an Array`
> cities = ["Chicago", "Los Angeles", "New York City"]

**.at method:**  
Takes an Integer argument and return the element in that position of an Array. The following lines of code show the various forms of the `.at` method and return the same output.  
`cities.at(2)`  
`cities.[](2)`   
`cities[2]`
>"New York City"

***Note:***
1. Ruby indexes the elements in an array starting at *zero*, that is, the first element of an array will have the index *zero*.
2. Trying to access an element using an index greater than the length of the array will give you `nil`.  
`cities.at(3) # => nil`
3. Using a negative index will retrieve elements from the end of the least.   
`cities.at(-1) # => "New York City"`  
`cities.at(-2) # => "Los Angeles"`  
`cities.at(-3) # => "Chicago"`   
`cities.at(-4) # => nil` 

**.first and .last methods:**  
Retrieve the first and the last element of an array.  
`cities.first # => "Chicago"`  
`cities.last) # => "New York City"`

**.index method:**  
Returns the index of an element.  
`cities.index("Los Angeles") # => 1`

**.count method:**  
Returns the number of elements in a list, when give no arguments. If given an argument, returns the number of times that arguments occurs in the array.
```
nums = [8, 3, 1, 19, 23, 3]
nums.count # => 6
nums.count(3) # => 2
nums.count(2) # => 0
```

**.reverse method:**  
Returns a new Array with the elements of the original Array but in the reversed order.  
`nums.reverse # => [3, 23, 19, 1, 3, 8]`

**.sort method:**  
Returns a new Array with the elements of the original Array but in the sorted in increasing order.  
`nums.sort # => [1, 3, 3, 8, 19, 23]`

**Example: Sorting an Array in decreasing order**
```
nums = [8, 3, 1, 19, 23, 3]
nums.sort # => [1, 3, 3, 8, 19, 23] 
nums.reverse # => [3, 23, 19, 1, 3, 8] 
nums.sort.reverse # => [23, 19, 8, 3, 3, 1], first sorts then reverses the Array. 
```
**.shuffle method:**  
Returns a new Array with the elements of the original Array but with the order shuffled randomly.  
`nums.shuffle # => [3, 23, 8, 19, 1, 3]`  
`nums.shuffle # => [19, 3, 1, 8, 3, 23]` 

**.sample method:**  
Returns a random element from the array.  
`nums.sample # => 23`  
`nums.sample # => 3`

**.min and .max methods:**  
Retrieve the elements of minimum and the maximum values in the array.  
`nums.min # => 1`  
`nums.max # => 23`

**.sum method:**  
Returns the sum of all the elements in the array.  
`nums.sum # => 57`
 
### Class Hash

list of objects represented with curly brackets, {}. Unlike Arrays, each cell is not automatically numbered but given a label by us.

#### Interlude: Class Symbol
Symbols are a sequence of characters and are used to to label something internally in the code. They are created by starting them off with a colon and follow the same naming conventions as variables, `:hello`.  
`:hello.class # => Symbol`  

**Creating a Hash:**  
`person1 = Hash.new`  
or  
`person2 = {}`

**.store method:**  
Adds elements to a Hash by taking two arguments, a label (or *key*) and a piece of data (or *value*). 
```
person1.store(:first_name, "Raghu")
person1.store(:last_name, "Betina")
person1.store(:role, "Instructor")
# => person1 = {:first_name=>"Raghu", :last_name=>"Betina", :role=>"Instructor"}
```
or we can fill up a hash by typing in the hash literal  
`person2 = { :first_name => "Jocelyn", :last_name => "Williams", :role => "Student" }`

***Note:***
1. Ruby represents each key/value pair by separating them with a `=>`, known as a "hash rocket."
2. If the value associated with a key already exists when you try to `.store` something under it, its value will be replaced.

**.fetch method:**  
Both `.fetch` and `.[]` can be used to retrieves the data held by a key.
`person1.fetch(:last_name)# => "Betina"`  
`person2.[:last_name] # => "Williams"` 

If `.fetch` is given key that is not present in the hash, it will throw an error. But `.[]` is given key that is not present in the hash, it returns nil. 

Fallback: pass in a second default argument that `.fetch` will return if the key is not present in the hash.  
`person1.fetch(:middle_name, "None provided") # => "None provided"`

### Conditionals

Basic Anatomy of multibranch `if` statements:
```
if condition1
  # do something if condition1 is true
elsif condition2
  # do something if condition2 is true
else # if both condition1 and condition2 were falsy
  # do something else
end
```

**Example:**
```
p "Type a number less than 10 and greater than 0:"
user_input = gets.chomp.to_i # gets user input, removes newline character, converts the string to integer. 
if user_input == 5 
  p "You win!" # Will print this if the user input is 5
elsif user_input < 10 && user_input > 0 # check if the user input is valid
  p "You lose!" # Will print this if the user input is between 1 and 9
else
  p "You didn't type in a valid number." # Will print this if the user input is not between 1 and 9
end
```
**Don't forget the `end` keyword.**

### Loops
**while statements:**  
`while` is similar to `if`. The difference is everytime the execution of the program reaches the `end` it jumps back and evaluates the *truthiness* of the condtion next to the `while` statement and decides whether or not to execute the code within the `while` loop.
```
while condition 
  # do something while condition is true
end # jump back to the while statement
```

**Example:**
```
limit = 5
while limit > 0 
  p limit
  limit = limit - 1
end 
```
>5  
>4  
>3  
>2  
>1  

***Note:***  
If the condition next to the `while` always evaluates to be "truthy," then the program will be stuck in a neverending loop, infamously known as an
**infinite loop**.

#### Blocks
**.times:**  
The `.times` method will execute the code within a block the number of times specified by the integer. A block of code is the code written in between the keywords `do` and `end`.
```
10.times do
  p "Hi"
end
```
The above block of code will print "Hi" 10 times all on newlines. 

To keep a track of the iteration number, `.times` can create a block variable that starts of counting the iteration number starting at *zero*. After each execution of the code within the block, the block variable is incremented by 1.  

```
10.times do |counter|
  p counter
end
```
The above block of code will print the numbers 0 to 9 all on newlines. 

#### Other methods
**.upto:**    
```
5.upto(10) do |counter|
  # do something
end
```
The above block of code starts the block variable `counter` at 5 and executes the block until counter is 10. 

**.downto:**  
`.downto` is similar to `.upto` except instead of incrementing the block varible, it decrements the block varible by 1.
```
10.downto(5) do |counter|
  # do something
end
```
The above block of code starts the block variable `counter` at 10 and executes the block until counter is 5. 

**.step:**
```
1.step(10, 3) do |counter|
  p counter
end
```
> 1  
> 4  
> 7  
> 10  

The above block of code starts the block variable `counter` at 1 and executes the block until counter is 10 but after each iteration the `counter` will be incremented by 3 instead of 1. `.step` can also be used to decrement the counter by a certain value. 
```
10.step(1, -4) do |counter|
  p counter
end
```
>10  
>6  
>2  

#### Looping through Arrays

**.each:**  
We could loop through an array with the `.times` method but the easier way of doing it is with the `.each` method. Given an array, the `.each` method will loop through each element of the array starting with the very first one. 
```
cities = ["Chicago", "LA", "NYC"]
cities.each do |city|
  p city
end
```
>"Chicago"  
>"LA"  
>"NYC"

The block variable `city` holds the value of the elements in the array `cities`. It starts with the first element `"Chicago"` and then changes with each interation, holding the value of the next element (`"LA"`) in the array and so on.
 
**.each_with_index:**  
To keep a track of the iteration number while looping through an array, `.each_with_index` creates an additional block variable that starts of counting the iteration number starting at *zero*. After each execution of the code within the block, the block variable is incremented by 1.  
```
cities.each_with_index do |city, count|
  p count.to_s + " " + city
end
```
>"0 Chicago"  
>"1 LA"  
>"2 NYC"

`city` holds the value of elements in the array `cities`. `count` holds the index of the element that `city` currently holds. 

***Note:***  
Variables created as a block variables can only be used within that block (between `do` and `end`). Using that variable outside that block will throw an error.
