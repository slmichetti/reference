# Python!

Characteristics:
	* case-sensitive
	* reads each line of code in order, from top to bottom 

Components of the language:
	* Module(s): a file that has a collection of useful code that can be used in other Python programs
		* You can create and import a module 
			* The new module must be in the same folder for you to import it 
 	* Methods: instructions in the code (instruction given to amy (ex turtlename.FORWARD) Forward is the method
	* Method Calls are instructions to find and run specific code
	* Comments are messages for human readers. The computer ignores comments when running the code. In Python, a comment begins with hashtag(#)

### Variables
	Are:
		* a connection between a name in the code and some data in the computer's memory
		* changeable of what data it refers to
			* Like a box w/ a label - use it to refer to whatever is in the box. Can take the label off and put it on another box

### Simple Statements
	Instructions of code for the turtle to carry out
	Different kinds of statements (import, naming turtle, instructions)
		Assignment Statements
		Import Statements
		Call Statements (calling another piece of code - giving istructions)

### Compound Statements
	> For Loop - has other statements inside of it (always indented statements underneath)
	> All used to control WHETHER, WHEN or HOW MANY TIMES a piece of code gets run
	> Typically code only runs through one time, but the loop causes it to run again
	> The order in which the code gest run is the **Control Flow**
	> Compound statements all alter the control flow
	> Using Loops alter it by changing how mnay times the code runs

### Range
	> Ways of expressing long lists more succinctly. Generate sequences of numbers to form a list. The given end point is never part of the generated list; generates a list of values, the legal indices for items of a sequence. 

### Strings
	> Bits of code comprised of a string of characters
	> Written inside "quotes" 

### Lists
	> Written with [square brackets] around it, and (,) commas separating the items. 
	> Can be integers or string ex: ["hello", "yellow", "stuff", "things"] 

### Loops
	
	> **for loop** repeats its block of code once for each item in a list or range. 
	> The number of times that code repeats is the number of items in that list or range. 
	> The loop has a loop variable which is set equal to each item, in order. 
	> Each time you call that fx it uses a changing variables
	> Use loops when you want to do the same thing repeatedly while changing the loop variables as inputs for that function 
	> The assignment happens in the first line of the for loop—but after that first line, you can assign a different value to the variable if we want to (using a regular assignment statement).

	**Nested Loops** 
	> A loop inside of another loop. Written by indenting under the first loop

	**While Loops**
	> Used when a condition needs to be checked each iteration, or to repeat a block of code forever

### Errors
	* Syntax Errors: These occur when you write something that doesn't make sense in the grammar of the language (ex: leaving off the : in the for loop)'
	* Usage Errors:  When you ask the computer to do something that doesn't make sense. 
	* Logic Errors: Like asking for the wrong thing. What you wrote isn't what you meant, so the computer doesn't do what you want you thought it would do.
	* TypeError: an error that involves the type of data being manipulated

### Functions

**Function definitions**
	> A function definition starts with the keyword def, the name of the function, and a parenthesized list of its arguments.

	> Name of a piece of code (input to that code)  EX range(100) - the input is put in parentheses. All methods are functions, but not all functions are methods (methods is a subset of functions)

	> Argument goes in () on the function call (the input passed to the function) 
	> Variable goes in () on the function def (also called parameters)
		> a parameter is a variable that is in the first line of a function definition

**Local (internal) variables**
	> A variable that is defined inside a function is called a local variable. Local variables can only be used inside the function where they are defined. The code outside the function can't refer to those variables. It'll stop with a NameError if it tries.
	A variable that is defined inside a function can be used only inside that function. Its local
	A variable defined outside of a function can be used anywhere - it has global scope	

**Input** 
   * Always returns a string
   * Will wait for a user response. input("Whats your name?"). User responds, enters and computer will return that string. 
	* the function call returns the string name; assign the return string to a variable name
		* name = input()
	* If using with a for loop (needs a list, range or other iterable value) - the string is made up of indvidual characters

**Print**
	* A standard libary function
	* Printed to the terminal
	* Can pass integers or arithmetic expressions
	* Print evaluates the expression, and then it prints the resulting value.
		* ex if you want 2+2 to print, you have to put it inside quotes to make it into a string
		* Inner functions get evaluated first

**String literal**
	* prints out the exact string of characters
	* use single and double quotes in string literals
		* use eiter to indicate a string - but cant combine different types
			* EOL = end of line error
	* Quotes tell python where the string starts and ends. But when dealing with strings that contain quotes (single or double or both), use \ (backslash) to tell python to treat it in an alternative way
	* Use \n - for a new line
	* With strings that contain both styles of quotes, use """ to enclose everything and python will treat the quotes as normal until it encounters the closing """

**len function** 
	* evaluates length
	* string = number of characters in the string 
	* no characters = empty string ""
	* len(list) is the number of items in the list; an empty list = 0
	* integers and other numeric values do not have a len

**Negative indexes**
You can use negative numbers as indexes. If word is a string, then word[-1] is the last character of that string, and word[-2] is the second-last, etc.


### ORDER OF OPERATIONS
	> Steps are performed in a particular order. 
	> Follows the same precedence rules for its mathematical operations that mathematics does.
			> Multiplication and division happen before addition and subtraction; expressions in parentheses are evaluated first

	> Arithmetic Expressions - a piece of code that resolves to some value. 
		> Also called evaluation or evaluates to
		> Operators: indicate what kind of operations is to be performed
		> Operands: the numbers or values we want to do those operations on
			> Almost anywhere you can use a number in your code, you can use an arthmetic expression in your code
### RANGE
	* Block of instructions in the code with the name "range" 
	* to get the code to run range(input) = a call statement or a "Call"
	* generates some output

### CONDITIONAL (if/then) sentences
	> Conditionals with if and else
	>The if keyword introduces a conditional statement. It has a condition, a true-or-false question. The block of code inside an if statement will either run, or not run, depending on whether the condition is true.

	| Operation | What it means 					|
	|:----------|:---------------------------------:|
	|: a == b	|: Is a equal to b?  				|
	|: a < b	|: Is a less than b? 				|
	|: a > b	|: Is a greater than b? 			|
	|: a <= b	|: Is a less than or equal to b? 	|
	|: a >= b	|: Is a greater than or equal to b?	|
	|: a != b	|: Is a not equal to b?				|

	> elif - else if
	> instead of nesting, change the if to elif (if / elif /else statement)
			
### MODULO
**MOD OPERATOR = %**
	* related to division; its the remainder
		* it divides 2 numbers and gives us the remainder (not the whole result)
		* x % y = remainder from x/y

### The random module
> The module called random is a collection of functions for adding randomness to Python programs. 
> It includes a lot of functions, most of them using advanced statistics.

	> **random.randint**
		> chooses an integer at random (like rolling a dice)
		> using this will provide a random number 

	> **random.choice**
		> takes one argument, which has to be a list, 
		> and it will choose an item from that list at random (such as a list of colors)