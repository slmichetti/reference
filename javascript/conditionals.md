## Conditionals
Write code to solve a problem
Algorithm - steps your code takes to solve a problem

Flowchart: visual diagram that outlines the solution to a problem through a series of logical statements. The order in which statements are evaluated and executed is called the control flow.

Using comparisons to compare two strings or numbers
a >= b  will evaluate to either true or false

### if..else statements
These allow you to execute certain pieces of code based on a condition, or set of conditions, being met. 

* the value inside the if statement is always converted to true or false
* code inside the statements are surrounded by curly braces{} to seperate the conditions and indicate which code should run
* can use just an if statement alone, but you cannot use an else statement on its own. Else require an if to work. 

```
The syntax of if is:

if(condition) {
  // what to happen
} else {
  // what to happen
}
```

```
if (/* this expression is true */) {
  // run this code
} else {
  // run this code
}

if (a >= b) {
	console.log("action");
} else {
	console.log("action");
}
```
The curly braces {} 
	whatever code is written inside of the curly braces is the code that will get executed

#### Multiple conditionals

In JavaScript, you can represent this secondary check by using an extra if statement called an else if statement. The else statement will act as the "default" condition in case all the other if statements are false.
```
var weather = "sunny";

if (weather === "snow") {
  console.log("Bring a coat.");
} else if (weather === "rain") {
  console.log("Bring a rain jacket.");
} else {
  console.log("Wear what you have on.");
}
```
```
var runner = "Kendyll";
var position = 2;
var medal; // will assign the variable value in the statements below

if(position === 1) {
  medal = "gold";
} else if(position === 2) {
  medal = "silver";
} else if(position === 3) {
  medal = "bronze";
} else {
  medal = "pat on the back";
}
```

## Logical Operators

The && symbol is the logical AND operator, and it is used to combine two logical expressions into one larger logical expression. If both smaller expressions are true, then the entire expression evaluates to true. If either one of the smaller expressions is false, then the whole logical expression is false.

**Logical Expressions**
* Logical expressions are similar to mathematical expressions, except logical expressions evaluate to either true or false. A comparison is just a simple logical expression.

* Similar to mathematical expressions that use +, -, *, / and %, there are logical operators &&, || and ! that you can use to create more complex logical expressions.

* Can be used in conjunction with boolean values (true and false) to create complex logical expressions
  * By combining two boolean values together with a logical operator, you create a logical expression that returns another boolean value. 

* Logical expressions are evaluated from left to right. Similar to mathematical expressions, logical expressions can also use parentheses to signify parts of the expression that should be evaluated first.

**&& means Logical AND**
  Ex: value1 && value2
  Returns true if both value1 and value2 evaluate to true

**|| means Logical OR**
  Ex: value1 || value2
  Returns true if either value1 or value2 (or even both) evaluates to true

**! means Logical NOT**
  Ex: !value1
  Returns the opposite ove value1. If value1 is true, then !value1 is false.


#### Truth Tables

Truth tables are used to represent the result of all the possible combinations of inputs in a logical expression. A represents the boolean value on the left-side of the expression and B represents the boolean value on the right-side of the expression.

The value of "A" is what determines the result of the logical expression, regardless of the value of "B".

Short-circuiting - behavior where later arguments in the logical expression aren't considered b/c the first argument already satisfies the condition.
    Logical AND - first value is false; the entire expression will always evaluate to True
    Logical OR - if the first value is true, the entire expression will always evaluate to True

**&& (AND)**
| A     | B     | A&&B  |
| --- - |:-----:| -----:|
| true  | true  | true  |
| true  | false | false |
| false | true  | false |
| false | false | false |

**|| (OR)**
| A     | B     | A||B  |
| --- - |:-----:| -----:|
| true  | true  | true  |
| true  | false | true  |
| false | true  | true  |
| false | false | false |


## Advanced Conditionals

### Truthy and Falsy

Every value in JavaScript has an inherent boolean value. When that value is evaluated in the context of a boolean expression, the value will be transformed into that inherent boolean value.

## Falsy Values

A value is **falsy** if it converts to false when evaluated in a boolean context. 
  Ex: An empty string "" is falsy because "" evaluates to false. 

**Falsy Values**
1. the Boolean value false
2. the null type
3. the undefined type
4. the number 0
5. the empty string ""
6. the odd value NaN (stands for "not a number")


## Truthy Values

A value is **truthy** if it converts to true when evaluated in a boolean context. 
  Ex: The number 1 is truthy because 1 evaluates to true.

** If it's not in the list of falsy values, then it's truthy!**


### Ternary Operator

The ternary operator provides you with a shortcut alternative for writing lengthy if...else statements.

```
conditional ? (if condition is true) : (if condition is false)
```

### Switch Statement

A switch statement is an another way to chain multiple else if statements that are based on the same value without using conditional statements. Instead, you just switch which piece of code is executed based on a value.

Switch statements can you be used on any type of data (not just numbers)

Each else if statement (option === [value]) is replaced with a case clause (case: [value]) and those clauses have been wrapped inside the switch statement

When the switch statment first evaluates, it looks for the first case clause whose expression evaluates to the same value as the result of the expression passed to the switch statement. Then, it transfers control to the case clause, executing the associated statements. 

**Break Statement**
The break statement can be used to terminate a switch statement and transfer control to the code following the terminated statement. By adding a break to each case clause, you fix the issue of the switch statement falling-through to other case clauses.

```
var option = 3;

switch (option) {
  case 1:
    console.log("You selected option 1.");
    break;
  case 2:
    console.log("You selected option 2.");
    break;
  case 3:
    console.log("You selected option 3.");
    break;
  case 4:
    console.log("You selected option 4.");
    break;
  case 5:
    console.log("You selected option 5.");
    break;
  case 6:
    console.log("You selected option 6.");
    break; // technically, not needed
}
```
#### Falling Through

In some cases, you might want to leverage the "falling-through" behavior of switch statements.
  Ex: where each successive tier builds on the next by adding more to the output. 

Ex:
```
var tier = "nsfw deck";
var output = "You’ll receive "

switch (tier) {
  case "deck of legends":
    output += "a custom card, ";
  case "collector's deck":
    output += "a signed version of the Exploding Kittens deck, ";
  case "nsfw deck":
    output += "one copy of the NSFW (Not Safe for Work) Exploding Kittens card game and ";
  default:
    output += "one copy of the Exploding Kittens card game.";
}

console.log(output);

Prints: You'll receive one copy of the NSFW (Not Safe for Work) Exploding Kittens card game and one copy of the Exploding Kittens card game.
```
