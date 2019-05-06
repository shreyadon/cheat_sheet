## Hello World

### Core syntax: 
`object.method`
or `object.method(args)` for methods that need arguments.

**.class method:**  
Returns the class of the object.  
`"Hello".class # => String`  
`2.class # => Integer`  
`2.3.class # => Float`

Creating a new variable of a Class:  
```
 var = Class.new
 str = String.new
 ```

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

**Math operations:**  
These will be covered in the Integer and Float sections.

**rand:**  
returns a random integer within a range when given an integer as an argument.  
`rand(3) # returns a whole number between 0 and 2`  
returns a random decimal between 0 and 1 when not given any argument.  
`rand # returns a decimal between 0 and 1`  

### Class String


Ignore: Add notes on String interpolation. 
**.concat (.+ / +) method:**  
Appends the given arguments to a string. when given an integer as an argument, it converts the integer into ASCII code.  
`"hi".concat(33)`
> "hi!"

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

**.upcase method:**  
Converts all lowercase letters to their uppercase counterparts in the given string.

`"hello".upcase`
> "HELLO"

**.downcase method:**  
Converts all the uppercase letters to their lowercase counterparts in th given string.

`"HI".downcase`
> "hi"

**.swapcase method:**  
Converts all the uppercase letters to their lowercase counterparts and lowercase letters to their uppercase counterparts in the given string.

`"Hi There".swapcase`
> "hI tHERE"

**.reverse method:**     
Returns a new String with the characters from the original String in reverse order.  
`"stressed".reverse`

> "desserts"

**.length method:**  
Returns the character length in a String as an integer.  
 `"hippopotamus".length`
> 12


**.chomp method:**  
When not given any argument, removes the "\n" (newline) character from the end of the string. when given an argument of a charcter or a string, it remove that argument from the **end** of the orginal string.  
`"Hey!\n".chomp`  
`"Hey!".chomp("!")`  
`"Hey!".chomp("y")`
>"Hey!"

>"Hey"

>"Hey!"

**.gsub method:**  
Substitutes the all occurances of the first argument with the second argument in original string.  
`"Hello".gsub("ello", "i")`
>"Hi"

**.to_i method:**  
Converts a string literal that contains a number to an integer.  
`"8".to_i`
>8

**.strip method:**  
Removes all leading and trailing whitespace in the string.  
`"   hi there ".strip`
>"hi there"

**.capitalize method:**  
Capitalizes the first character of a string.  
`"capitalize".capitalize`
>"Capitalize"

**.split method:**  
Splits a string into an substrings and creates an Array of these substrings. when not given argument, .split uses whitespace to divide the string. when given an argument, .split uses that argument to divide the string.  
`"Hello hi byebye".split`
>["Hello", "hi", "byebye"]

`"one!two!three!".split("!")`
>["one", "two", "three"]`

### Class Integer
whole numbers

Math Operations for the Integer Class:  
`12 + 5 # => 17`  
`12 - 5 # => 7 `  
`12 * 5 # => 60`  
`12 / 5 # => 2`  
The `/` operator for integers only returns a whole number and omits the remainder.

`%` **(modulus) operator:**  
Returns the remainder from a division operation.  
`13 / 5 # => 3`

`**` **operator:**  
Raises a number to a power.  
`3 ** 2 # => 9`  
`2 ** 3 # => 8`



**.odd? and .even? methods:**  
Returns a *boolean* based on whether the integer is odd or even.  
`7.odd?`
>true

`7.even?`
>false

**.to_s method:**  
Converts an integer to a string literal.  
`8.to_s`
>"8"

`"There are " + 7.to_s + " pineapples."`
>"There are 7 pineapples"

**.to_f method:**  
converts an integer to a float(decimal).  
`7.to_f`
>7.0


### Class Float
decimals

Math Operations for the Float Class:  
Standard operations are similar to those for the Integer class. The only exception is the `/` operator which returns fractional results.  
`12 / 5 # => 2`  
`12.0 / 5.0 # => 2.4`  
`12 / 5.0 # => 2.4`  
`12.0 / 5 # => 2.4`  

`**` **operator:**  
The `**`operator for Floats can be used to calculate roots.  
`9 ** 0.5 # => 3.0`  
`8 ** (1/3.0)# => 2.0`  

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

### Class Date

**Creating a Date:**  
To use the Date class in a Ruby program, we need to say:  
`require "date"`  

**Date.new**  
Use the `.new` method to create a new instance of a Date object. The `.new` method can be used with or without argument. When given no arguments, the default date is set to ***Jan 1st, -4712 BCE***.
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

list of objects represeted with square brackets, [].


**Creating an Array:**  
`.new` initializes a new empty Array.  
`cities = Array.new # => cities = []`  
or  
`cities = [] # => cities = []` 

**push:**  
Adds elements to an Array. 
```
cities.push("Chicago")
cities.push("Los Angeles")
cities.push("New York City")
```
or  
`cities = ["Chicago", "Los Angeles", "New York City"]`
> cities = ["Chicago", "Los Angeles", "New York City"]

**.at method:**  
Takes an Integer argument and return the element in that position of an Array. The following lines of code show the various forms of the `.at` method and return the same output.  
`cities.at(2)`  
`cities.at[](2)`  
`cities.[2]`  
>"New York City"

***Notes:***
1. Ruby indexes the elements in an array starting at *zero*.
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
```

**.reverse method:**  
Returns a new Array with the elements of the original Array but in the reversed order.  
`nums.reverse # => [3, 23, 19, 1, 3, 8]`

**.sort method:**  
Returns a new Array with the elements of the original Array but in the sorted in increasing order.  
`nums.sort # => [1, 3, 3, 8, 19, 23]`

**.shuffle method:**  
Returns a new Array with the elements of the original Array but with the order shuffled randomly.  
`nums.shuffle # => [3, 23, 8, 19, 1, 3]`

**.sample method:**  
Returns a random element from the array.
`nums.sample # => 23`

**.min and .max methods:**  
Retrieve the elements of minimum and the maximum values in the array.  
`nums.min # => 1`  
`nums.last # => 23`

**.sum method:**  
Returns the sum of all the elements in the array. 
`nums.sum # => 57`
