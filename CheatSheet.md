## Hello World

### Core syntax: 
`object.method`
or `object.method(args)` for methods that need arguments.

**.class method:**  
Returns the class of the object.  
`"Hello".class # => String`  
`2.class # => Integer`  
`2.3.class # => Float`


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

**rand**  
returns a random integer within a range when given an integer as an argument.  
`rand(3) # returns a whole number between 0 and 2`  
returns a random decimal between 0 and 1 when not given any argument.  
`rand # returns a decimal between 0 and 1`  

Creating a new variable of a Class:  
```
 var = Class.new
 str = String.new
 ```

### Class String

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
