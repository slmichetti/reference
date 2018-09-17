## Function Expressions

Function Expression: When a function is assigned to a variable. The function can be named, or anonymous. Use the variable name to call a function defined in a function expression.

```
// anonymous function expression
var doSomething = function(y) {
  return y + 1;
};
```
```
// named function expression
var doSomething = function addOne(y) {
  return y + 1;
};
```
```
// for either of the definitions above, call the function like this:
doSomething(5);
```
Returns: 6

**Pass a function into another function inline**
This is commonly used and is helpful streamlining your code

```
// function declaration that takes in two arguments: a function for displaying
// a message, along with a name of a movie
function movies(messageFunction, name) {
  messageFunction(name);
}
```
```
// call the movies function, pass in the function and name of movie
movies(function displayFavorite(movieName) {
  console.log("My favorite movie is " + movieName);
}, "Finding Nemo");
```
