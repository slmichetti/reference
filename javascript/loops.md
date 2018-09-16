## Loops

Many different types of loops, but they all essentally do the same thing - they repeat an action some number of times.

Three main pieces of informaiton that any loop should have:
* **When to start**: The code that sets up the loop - defining teh starting value of a variable or instance
* **When to stop** The logical condition to test whether the loop should continue
* **How to get to the next item** The incrementing or decrementing step for example.

Ex:
```
var start = 0; // when to start
while (start < 10) { // when to stop
  console.log(start);
  start = start + 2; // how to get to the next item
}
```

### While Loops

Loops let you iterate over values and repeatedly run a block of code

```
while (x <= 10000) {
var x = 1;
console.log(x + "mississippi!");
x = x + 1
}
```

ex:
```
var x = 10;
while (x <= 25) {
  console.log('Printing out x = ' + x);
  x = x + 2;
}
```
The code in this example runs 8 times

### For Loops

The for loop explicitly forces you to define the start point, stop point, and each step of the loop. You'll receive an Uncaught SyntaxError: Unexpected token ) if you leave out any of the three required pieces.

```
for ( start; stop; step ) {
  // do this thing
}
```

Ex: for loop that prints out values from 0 to 5. **semicolons separate the different statements of the for loop**
```
var i = 0; i < 6; i = i + 1

for (var i = 0; i < 6; i = i + 1) {
  console.log("Printing out i = " + i);
}
```

### Nested Loops

Similar to conditional statements, you can nest loops inside one another.  Nested loops dont change the functionality, but add a layer of complexity. 

Ex:
```
for (var x = 0; x < 3; x = x + 1) {			*\ loops through then goes to y and resolves until its 
	for (var y = 0; y < 2; y = y + 1) {  	*\ no longer true; then back up to the first loop and
		console.log(x + ", " + y);			*\ then back through the second loop until not true
	}										*\ again
}
```
For each value of x in the outer loop, the inner for loop executes completely. The outer loop starts with x = 0, and then the inner loop completes it's cycle with all values of y:
```
x = 0 and y = 0, 1, 2 // corresponds to (0, 0), (0, 1), and (0, 2)
```
Once the inner loop is done iterating over y, then the outer loop continues to the next value, x = 1, and the whole process begins again.
```
x = 0 and y = 0, 1, 2 // (0, 0) (0, 1) and (0, 2)
x = 1 and y = 0, 1, 2 // (1, 0) (1, 1) and (1, 2)
x = 2 and y = 0, 1, 2 // (2, 0) (2, 1) and (2, 2)
etc.
```
### Increment and decrement

Increasing or decreasing the value of a variable to step through the loop

Increment operators:
```
x++ or ++x // same as x = x + 1 
x-- or --x // same as x = x - 1
x += 3 // same as x = x + 3
x -= 6 // same as x = x - 6
x *= 2 // same as x = x * 2
x /= 5 // same as x = x / 5
```

x++ - return x and then increment it; ++x increments it before the value is returned back to you
```
var x = 0;
x++
0
then x increments to 1

++x
2
```

Most cases these are interchangeable. The values returned by the program you're writing will detrmine which order you should use.


