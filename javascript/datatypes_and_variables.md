## Developer Tools

Used as a sandbox to test code
Debug and test code

All browsers come with built-in javascript engines
Javascript consoel - allows you to print strings and execute code in the browswer
Can use javascript to add styles and animations to a site

## Data Types
Data and data types are the building blocks of any programming language b/c they help organize info and determine how programs will run

### Numbers
* Includes any positive or negative integer, as well as decimals

### Arthmetic Operations
* Perform calculations with number by typing out an expression
* Compare numbers to see if one is greater than/less than/ or equal to another

Operator	Meaning
	<	Less than
	>	Greater than
	<=	Less than or Equal to
	>=	Greater than or Equal to
	==	Equal to
	!=	Not Equal to

## Comments
Comments are used to help clarify the meaning of your code in a human-friendly language
In javascript written with  double forward-slash 
// Anything written on the same line after the // will not be executed or displayed. 
	``` //comment
	/*
	block of comment
	*/ ```


## Strings
Quotes signify the string. Can be single or double, but quotes need to be consistent

#### String Concatenation
If you want to have a space in between two words, you need to explicitly add a space! It will not be added automatically for you.

strings can be any collection of characters that are surrounded by quotation marks. The "+ 5*10" are just characters inside the quotation marks, so the interpreter will assume the whole object is a string, and output the result as a string!
"Hello," + " New York City" returns "Hello New York City"
```
"Hello + 5*10" 
returns
"Hello +5*10"
```



Implicit Type Coercion = a feature of javascript

## Variables
Storing data to use it later through the use of variables
Not limited to storing numeric values - can store any data

var variableName = (assignment operator) the value you want to assign to the variable
	ex: var greeting = "Hello";
	reuse the variable
	greeting + "World!";
	returns Hello World!

	You can also change the start of the greeting by reassigning a new string value to the variable greeting.

### Naming Conventions

When you create a variable, you write the name of the variable using camelCase (the first word is lowercase, and all following words are uppercase). Also try to use a variable name that accurately, but succinctly describes what the data is about.

``` 
var totalAfterTax = 53.03; // uses camelCase if the variable name is multiple words
var tip = 8; // uses lowercase if the variable name is one word 
```

### Indexing

To access an individual character, you can use the character's location in the string, called its index. Just put the index of the character inside square brackets (starting with [0] as the first character) immediately after the string.

ex: console.log(quote[6]) or alternatively
quote.charAt(6) 

### Escape Strings

Instances where you want to create a string that contins more than just numbers and letters (ex quotes in a string)
  To use quotes inside a string, you use the backslash charater (\)

 The backslash is used to escape other characters. 
  Escaping a character tells JavaScript to ignore the character's special meaning and just use the literal value of the character. 

SPECIAL CHARACTERS (to use with backslash within a string)
 Code	Character
 \\		\ (backslash)
 \"		'' (double quote)
 \'		' (single quote)
 \n		newline
 \t		tab

newline and tab both add whitespace to your Strings. A newline character will add a line break and a tab character will advance your line to the next tab stop.

### Comparing Strings

Comparison operators of == and != can be used with strings. 
Case matters when comparing strings.
When checking if a string is "greater than" or "less than" another string, JavaScript compares individual characters using a numerical value. Each character is assigned a numerical value that essentially corresponds to the character's location in an ASCII table: http://www.ascii-code.com/

## Booleans

Whenever you compare data, the result of the data will always be True or False (Booleans)
yes/no, true/false

### Null, Undefined and NaN

Null = value of nothing; totally empty
	set a variale to the value of null, it will return null Null will be returned when you purposefully assign the value to nothing.

Undefined = absence of value; does not have a value, not even a value of nothing. Undefined will be returned to you if you didn't assign a value to something.

NaN = Not-A-Number; returned indicating an error with number operations. Ex. you wrote some code taht performed a math calculation, and the calculation failed to produce a vaild number, NaN might be returned. 


#### Equality

If you use == and != in situations where the data you’re comparing is mixed, it can lead to some interesting results due to:

**Implicit type coercion**
JavaScript is known as a loosely typed language.

Basically, this means that when you’re writing JavaScript code, you do not need to specify data types. Instead, when your code is interpreted by the JavaScript engine it will automatically be converted into the "appropriate" data type. This is called implicit type coercion and you’ve already seen examples like this before when you tried to concatenate strings with numbers.

A strongly typed language is a programming language that is more likely to generate errors if data does not closely match an expected type. Because JavaScript is loosely typed, you don’t need to specify data types; however, this can lead to errors that are hard to diagnose due to implicit type coercion.

When you use the == or != operators, JavaScript first converts each value to the same type (if they’re not already the same type); this is why it's called "type coercion"! This is often not the behavior you want, and **it’s actually considered bad practice to use the == and != operators when comparing values for equality.**

Strict Equality
In JavaScript it’s better to use strict equality to see if numbers, strings, or booleans, etc. are identical in type and value without doing the type conversion first. To perform a strict comparison, simply add an additional equals sign = to the end of the == and != operators.
```"1" === 1 
```

**Semicolons**
Semicolons are used at the end of each line - they make it clear where one statement ends and another begins (**valid Javascript but not recommended**) Not adding semicolons to the end of each line can cause bugs and errors in your programs. 


``` var totalAfterTax = 53.03; var tip = 8; // this is correct! 
```

