## Arrays

 An array is useful because it stores multiple values into a single, organized data structure. You can define a new array by listing values separated with commas between square brackets [].

 ```
 // creates a `donuts` array with three strings
var donuts = ["glazed", "powdered", "jelly"];
```
```
/ creates a `mixedData` array with mixed data types
var mixedData = ["abcd", 1, true, undefined, null, "all the things"];
```
```
// creates a `arraysInArrays` array with three arrays
var arraysInArrays = [
  [1, 2, 3], 
  ["Julia", "James"], 
  [true, false, true, false]
];
```

### Indexing 

Elements are indexed starting at position 0.
To access an element in an array, use the name of the array followed by square brackets containing the index of the value you want to access
	An undefined error will return if you try to access an element at an index that does not exist
```
var donuts = ["glazed", "powdered", "sprinkled"];
console.log(donuts[0]); // "glazed" is the first element in the `donuts` array
```

**Change the value of an element in an array**
```
donuts[1] = "glazed cruller"; // changes the second element in the `donuts` array to "glazed cruller"
console.log(donuts[1]); 
```

### Array Properties and Methods

reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array

**Array.length**
Find the length of an array by using its length property.
```
var donuts = ["glazed", "powdered", "sprinkled"];
console.log(donuts.length);
Prints: 3
```

To access the length property, type the name of the array, followed by a period . (you’ll also use the period to access other properties and methods), and the word length. The length property will then return the number of elements in the array.

### Modifying an Array

**Push**
push() method to add elements to the end of an array.
With the push() method you need to pass the value of the element you want to add to the end of the array. Also, the push() method returns the length of the array after an element has been added.

ex:
```
var donuts = ["glazed", "chocolate frosted", "Boston creme", "glazed cruller", "cinnamon sugar", "sprinkled"];

donuts.push("powdered"); // pushes "powdered" onto the end of the `donuts` array

Returns: 7
donuts array: ["glazed", "chocolate frosted", "Boston creme", "glazed cruller", "cinnamon sugar", "sprinkled", "powdered"]
```


**Pop**
pop() method to remove elements from the end of an array.
With the pop() method you don’t need to pass a value; instead, pop() will always remove the last element from the end of the array. Also, pop() returns the element that has been removed in case you need to use it.

ex:
```
var donuts = ["glazed", "chocolate frosted", "Boston creme", "glazed cruller", "cinnamon sugar", "sprinkled", "powdered"];

donuts.pop(); // pops "powdered" off the end of the `donuts` array
donuts.pop(); // pops "sprinkled" off the end of the `donuts` array
donuts.pop(); // pops "cinnamon sugar" off the end of the `donuts` array
Returns: "cinnamon sugar"
donuts array: ["glazed", "chocolate frosted", "Boston creme", "glazed cruller"]
```
```
var donuts = ["glazed", "chocolate frosted", "Boston creme", "glazed cruller", "cinnamon sugar", "sprinkled", "powdered"];
donuts.pop(); // the `pop()` method returns "powdered" because "powdered" was the last element on the end of `donuts` array
Returns: "powdered"
```

**Splice()**
splice() is another method that allows you to add and remove elements from anywhere within an array.
Splice() lets you specify the index location to add new elements, as well as the number of elements you'd like to delete (if any).

The first argument represents the starting index from where you want to change the array, the second argument represents the numbers of elements you want to remove, and the remaining arguments represent the elements you want to add.

Reference(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

ex:
```
var donuts = ["glazed", "chocolate frosted", "Boston creme", "glazed cruller"];
donuts.splice(1, 1, "chocolate cruller", "creme de leche"); // removes "chocolate frosted" at index 1 and adds "chocolate cruller" and "creme de leche" starting at index 1
Returns: ["chocolate frosted"]
donuts array: ["glazed", "chocolate cruller", "creme de leche", "Boston creme", "glazed cruller"]
```

### Array Loops

Once the data is in the array, you want to be able to efficiently access and manipulate each element in the array without writing repetitive code for each element.

To loop through an array, you can use a variable to represent the index in the array, and then loop over that index to perform manipulations.

ex: In this example, the variable i is being used to represent the index of the array. As i is incremented, you are stepping over each element in the array starting from 0 until donuts.length - 1 (donuts.length is out of bounds).

```
var donuts = ["jelly donut", "chocolate donut", "glazed donut"];

// the variable `i` is used to step through each element in the array
for (var i = 0; i < donuts.length; i++) {
    donuts[i] += " hole";
    donuts[i] = donuts[i].toUpperCase();
}
donuts array: ["JELLY DONUT HOLE", "CHOCOLATE DONUT HOLE", "GLAZED DONUT HOLE"]
```
**forEach()**
The forEach() method gives you an alternative way to iterate over an array, and manipulate each element in the array with an inline function expression.

forEach() method iterates over the array without the need of an explicitly defined index. In the example above, donut corresponds to the element in the array itself. 
ex:
```
var donuts = ["jelly donut", "chocolate donut", "glazed donut"];

donuts.forEach(function(donut) {
  donut += " hole";
  donut = donut.toUpperCase();
  console.log(donut);
});
Prints:
JELLY DONUT HOLE
CHOCOLATE DONUT HOLE
GLAZED DONUT HOLE
```

This is different from a for or while loop where an index is used to access each element in the array:
```
for (var i = 0; i < donuts.length; i++) {
  donuts[i] += " hole";
  donuts[i] = donuts[i].toUpperCase();
  console.log(donuts[i]);
}
```

**Parameters**
he function that you pass to the forEach() method can take up to three parameters. In the video, these are called element, index, and array, but you can call them whatever you like.

The forEach() method will call this function once for each element in the array (hence the name forEach.) Each time, it will call the function with different arguments. 
The **element parameter** will get the value of the array element. 
The **index parameter** will get the index of the element (starting with zero). 
The **array parameter** will get a reference to the whole array, which is handy if you want to modify the elements.

**map()**
the map() method, you can take an array, perform some operation on each element of the array, and return a new array.

The map() method accepts one argument, a function that will be used to manipulate each element in the array.
ex:
```
var donuts = ["jelly donut", "chocolate donut", "glazed donut"];

var improvedDonuts = donuts.map(function(donut) {
  donut += " hole";
  donut = donut.toUpperCase();
  return donut;
});
donuts array: ["jelly donut", "chocolate donut", "glazed donut"]
improvedDonuts array: ["JELLY DONUT HOLE", "CHOCOLATE DONUT HOLE", "GLAZED DONUT HOLE"]
```

#### Arrays in Arrays

If you wanted to loop over the donut box and display each donut (along with its position in the box!) you would start with writing a for loop to loop over each row of the box of donuts:

```
var donutBox = [
  ["glazed", "chocolate glazed", "cinnamon"],
  ["powdered", "sprinkled", "glazed cruller"],
  ["chocolate cruller", "Boston creme", "creme de leche"]
];

// here, donutBox.length refers to the number of rows of donuts
for (var row = 0; row < donutBox.length; row++) {
  console.log(donutBox[row]);
}
Prints:
["glazed", "chocolate glazed", "cinnamon"]
["powdered", "sprinkled", "glazed cruller"]
["chocolate cruller", "Boston creme", "creme de leche"]
```

Since each row is an array of donuts, you next need to set up an inner-loop to loop over each cell in the arrays.
```
for (var row = 0; row < donutBox.length; row++) {
  // here, donutBox[row].length refers to the length of the donut array currently being looped over
  for (var column = 0; column < donutBox[row].length; column++) {
    console.log(donutBox[row][column]);
  }
}
Prints:
"glazed"
"chocolate glazed"
"cinnamon"
"powdered"
"sprinkled"
"glazed cruller"
"chocolate cruller"
"Boston creme"
"creme de leche"
```

