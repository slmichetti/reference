## Ternary Operator

The ternary operator provides you with a shortcut alternative for writing lengthy if...else statements.

```
conditional ? (if condition is true) : (if condition is false)
```

To use
* Provide a conditional statement on the left side of the ?
* Between the ? and : write the code that would run if hte condition is true
* On the right hand side of the : write the code that would run if the condition is false

This code replaces the conditional and handles the variable assignment for color

Ex:
from this:
```
var isGoing = true;
var color;

if (isGoing) {
  color = "green";
} else {
  color = "red";
}

console.log(color);

Prints: "green"
```

To this:
```
var isGoing = true;
var color = isGoing ? "green" : "red";
console.log(color);

Prints "green"
```

**Code Breakdown**
The condition isGoing is placed on the left side of the ?. Then, the first expression, after the ?, is what will be run if the condition is true and the second expression after the, :, is what will be run if the condition is false.

Ex:
```
var adult = true;
var preorder = true;

console.log("It costs $" + (adult ? "40.00" : "20.00") + " to attend the concert. Pick up your tickets at the " + (preorder ? "will call" : "gate") + ".");
```
Prints: It costs $40 to attend the concert. Pick up your tickets at the will call. 