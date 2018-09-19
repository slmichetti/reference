## Intro to Functions

Functions - lines of code, packaged together, that you can use and reuse when you need them
Function is given some data, performs operations on the data nad returns the altered data.
* Functions sometimes take parameters, functionName(parameter)
	* Multiple parameters get separated by commas functionName(parameter, parameter, parameter)
* Also possible to have functions with no parameters functionName()
Ability to generalize code for a variety of inputs
```
function reverseString(reverseMe) {
	var reversed = "";
	for (var i = reverseMe.length - 1; i >+ 0; i--) {
		reversed += reversedMe[i];
	}
	return reversed;
}

console.log(reverseString("Julia"));
```

### Return Statements

Write a return statement by using the **return** keyword followed by the expression or value that you want to return.

```
// declares the sayHello function
function sayHello() {
  var message = "Hello!"
  return message; // returns value instead of printing it
}
```

### Running a Function

To get your function to do something, you must call the function using the functionName, followed by the parentheses with any arguments that are passed into it. 
```
// declares the sayHello function
function sayHello() {
  var message = "Hello!"
  return message; // returns value instead of printing it
}

// function returns "Hello!" and console.log prints the return value
console.log(sayHello());

Prints: "Hello!"
```

### Parameters vs Arguments

Key difference between these is where they show up in the code

**Parameter**: is always going to be a variable name and appears in the function declaration

**Argument**: is always going to be a value and will always appear in the code when the function is called or invoked. 

**Functions** package up code so you can easily use (and reuse) a block of code. **Parameters** are variables that are used to store the data that's passed into a function for the function to use. **Arguments** are the actual data that's passed into a function when it is invoked. The **function body** is enclosed inside curly brackets. **Return statements** explicitly make your function return a value. You **invoke** or **call** a function to have it do something. 
```
// x and y are parameters in this function declaration
function add(x, y) {
  // function body
  var sum = x + y;
  return sum; // return statement
}

// 1 and 2 are passed into the function as arguments
var sum = add(1, 2);

Returns: 3
```

### Returning vs Logging

Return and print are not the same thing.
* Printing a value to the console only displays a value (can be used for debugging purposes), but the value it displays cant really be used for anything more than that
	* Use only the console.log to test your code in the Javascript console

In the console - undefined i always going to return some value back to the caller. If you don't explicitly define a return value, the function will return undefined by default.

Function output
console.log - prints a value
return - use to stop execution of a function and returns a value back to the caller. If value is not defined, it will return undefined.

* A function is always going to return something
* Console.log is not the same thing as a return statement. 

```
function square(x) {
  return x * x;
}

function subtractFour(x) {
  return square(x) - 4;
}

console.log(subtractFour(5));

prints: 21
```
```
function sleep() {
  console.log("I'm sleepy!");
  return "zzz";
  return "snore";
}

sleep();

returns: zzz /* it will exit the function after zzz, so snore will never return
```

### Using Return Values

A function's return value can be stored in a variable or reused throughout your program as a function argument.

```
// returns the sum of two numbers
function add(x, y) {
  return x + y;
}


// returns the value of a number divided by 2
function divideByTwo(num) {
  return num / 2;
}


var sum = add(5, 7); // call the "add" function and store the returned value in the "sum" variable
var average = divideByTwo(sum); // call the "divideByTwo" function and store the returned value in the "average" variable
```
```
function addTen(x) {
  return x + 10;
}

function divideByThree(y) {
  return y / 3;
}

var result = addTen(2);
console.log(divideByThree(result));

var result = addTen(2); // the result variable will be assigned the value of 12
divideByThree(result); // passes the value of 12 as an argument into the divideByThree function
```

### Scope

The part of the program where a particular identifier is visible or accessible

in-scope vs out-of-scope

#### Two kinds of scope
**Global Scope**
If you define an identifier outside all of your functions, its part of the global scope.
Variable can be accessed everywhere within your program

**Function Scope**
Identifiers defined inside of a function; its visible everywhere inside the function it was defined in, including functions inside that function.

When trying to access an identifier, the JavaScript Engine will first look in the current function. If it doesn't find anything, it will continue to the next outer function to see if it can find the identifier there. It will keep doing this until it reaches the global scope.

Global identifiers are a bad idea. They can lead to bad variable names, conflicting variable names, and messy code.

#### Shadowing

Scope overriding or shadowing
Can result from variables being assigned two different values in different scopes
Global scope will be reassigned to function scope

To avoid this, create a different variable inside the function to make it relative to the function scope

ex:
```
var x = 1;

function addTwo() {
  x = x + 2;
}

addTwo();
x = x + 1;
console.log(x);

prints: 4
```
The global variable x is assigned the value of 1.
Then, the function addTwo() increments the variable by 2.
Next, the variable is incremented by 1.
Finally, it's printed out using console.log.


ex with function var added:
```
var x = 1;

function addTwo() {
  var x = x + 2;
}

addTwo();
x = x + 1;
console.log(x);

prints: 2
```
The global variable x is incremented by 1. Since the global variable's original value was 1, and it was incremented by 1, console.log will print out 2.

The variable assignment inside the function addTwo() only has function scope, so its affect is not reflected outside the function.

### Hoisting

Generally you have to declare a function before calling it.

**Hoisting** before any code is executed, all function declarations are "hoisted" to the top of the current scope. This is done as the code is being interpreted (visually the code doesn't change)
Also happens with variable declarations

Can cause an error b/c when the value is defined, it doesn't get hoisted with the declarations.
```
sayHi("Julia");

function sayHi(name) {
  console.log(greeting + " " + name);
  var greeting = "Hello";
}

Prints: undefined Julia b/c the assignment isn't hoisted with the declaration.
```

** Remember**
* JavaScript hoists function declarations and variable declarations to the top of the current scope.
* Variable assignments are not hoisted.
* Declare functions and variables at the top of your scripts, so the syntax and behavior are consistent with each other.

**To avoid these bugs:
Declare functions at the top of the scripts and variables at the top of the functions**

### Function Expressions

Function Expressions = Functions stored in variables
Function keyword no longer has a name - anonymous function.  To access the function, just use the variable name and you'll see the function returned back to you.

Ex:
```
var catSays = function(max) {
  var catMessage = "";
  for (var i = 0; i < max; i++) {
    catMessage += "meow ";
  }
  return catMessage;
};
```

** Be careful of hoisting when using function expressions**
All function declarations are hoisted and loaded before the script is actually run. Function expressions are not hoisted, since they involve variable assignment, and only variable declarations are hoisted. The function expression will not be loaded until the interpreter reaches it in the script.

```
function cat() {
	*/ console.log(meow(2));
	console.log(purr());
	var meow = function(max) {
		var catMessage = "";
		for(var i = 0; i < max; i++) {
			catMessage += "meow";
		}
		return catMessage;
	}
	function purr() {
		return "purrrr!";
	}
}
cat();
```

function purr gets hoisted to the top (above console.log(meow(2)) and returns an error b/c meow is not a function(...)

instead the console.log(meow) should be console.log(purr());


### Patterns with Function Expressions

**Callback** is a function that is passed into another function. (Named function expression vs anonymous expression)
Set up your function to accept a callback function. Use the variable name to call the function (not the function name)
Ex:
```
// function expression catSays
var catSays = function(max) {
  var catMessage = "";
  for (var i = 0; i < max; i++) {
    catMessage += "meow ";
  }
  return catMessage;
};

// function declaration helloCat accepting a callback
function helloCat(callbackFunc) {
  return "Hello " + callbackFunc(3);
}

// pass in catSays as a callback 	
helloCat(catSays);
```

**Inline function expression** is when a function is assigned to a variable. In JavaScript, this can also happen when you pass a function inline as an argument to another function.
Ex without inline:
```
/ Function expression that assigns the function displayFavorite 
// to the variable favoriteMovie
var favoriteMovie = function displayFavorite(movieName) {
  console.log("My favorite movie is " + movieName);
};

// Function declaration that has two parameters: a function for displaying
// a message, along with a name of a movie
function movies(messageFunction, name) {
  messageFunction(name);
}

// Call the movies function, pass in the favoriteMovie function and name of movie
movies(favoriteMovie, "Finding Nemo");

Returns: My favorite move is Finding Nemo
```
using inline you bypass the first assignent of the function by passing the function to the movies() function inline line:
```
// Function declaration that takes in two arguments: a function for displaying
// a message, along with a name of a movie
function movies(messageFunction, name) {
  messageFunction(name);
}

// Call the movies function, pass in the function and name of movie
movies(function displayFavorite(movieName) {
  console.log("My favorite movie is " + movieName);
}, "Finding Nemo");
Returns: My favorite movie is Finding Nemo
```

When to use anonymous inline function expressions:
Anonymous inline function expressions are often used with function callbacks that are probably not going to be reused elsewhere. Yes, you could store the function in a variable, give it a name, and pass it in like you saw in the examples above. However, when you know the function is not going to be reused, it could save you many lines of code to just define it inline.

