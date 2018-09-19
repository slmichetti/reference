## Objects

One of the most important data structures in javascript. Allows you to wrap up pieces of related data in a functionality into a single container ("encapsulating" all the data associated with a particular thing inside a single object). They have properties (information about the object) and methods (functions or capabilities the object has).

Create an object - by creating a variable and assign to empty braces {}
typeof (operator) - returns a string that tells you the data type
typeof object{}
assign key value pairs for each piece of data (ex: color) add property that describes it and add a starting value. Something the object can do is a method (a fucntion that is associated with an object (ex push and pop with arrays)).


```
typeof is an operator that returns the name of the data type that follows it:

typeof "hello" // returns "string"
typeof true // returns "boolean"
typeof [1, 2, 3] // returns "object" (Arrays are a type of object)
typeof function hello() { } // returns "function"
```

var umbrella = {
	color: "pink", 
	isOpen: false
};

**Primitive Data Types**
strings  numbers  booleans  undefined  null

typeof {1, 2, 3};
returns object

Objects are a data structure in javascript that lets you store any kind of data value about a particular thing, and helps you keep track of that data by using a "key."

Ex: data about a Person
Instead of defining all the data about a person in isolated variables, objects let you group them together; stored as key value pairs in {}
common to format objects with each key value pair on its own line

Object-literal notation
* The "key" (representing a property or method name) and its "value" are separated from each other by a colon
* The key: value pairs are separated from each other by commas
* The entire object is wrapped inside curly braces { }.
```
var sister = {
  name: "Sarah", 
  age: 23,
  parents: [ "alice", "andy" ],
  siblings: ["julia"],
  favoriteColor: "purple",
  pets: true
};
```
Like how you can look up a word in the dictionary to find its definition, the key in a key:value pair allows you to look up a piece of information about an object. 
```
// two equivalent ways to use the key to return its value
sister["parents"] // returns [ "alice", "andy" ]
sister.parents // also returns ["alice", "andy"]
```
Using sister["parents"] is called **bracket notation** (because of the brackets!) and using sister.parents is called **dot notation** (because of the dot!).

Methods
Syntax for calling methods in the objects is similar
```
var sister = {
  name: "Sarah",
  age: 23,
  parents: [ "alice", "andy" ],
  siblings: ["julia"],
  favoriteColor: "purple",
  pets: true,
  paintPicture: function() { return "Sarah paints!"; }
};

sister.paintPicture();

    Returns: "Sarah paints!"
```
or by using the name property:
```
sister.name

    Returns: "Sarah"
```

### Naming Conventions for Variable Names and Property Names

* Quotes are valid around property names, but not required. Quotes can sometimes mask potential problems when you're naming object properties

* Dont use numbers as the first character in your property names. It works with bracket notation, but limits you with dot notation (and is considered bad practice)

* Avoid using spaces or hyphens when creating property names - results in an error when using dot notation. If you want to use multi-word properties, use camelCasing. 

```
var user = {
  email: "user@example.com",
  firstName: "first",
  lastName: "last"
};

console.log(user.email); or
consoel.log(user["email"]);
```

Create an object for a red honda civic:
```
var car = { manufacturer: "honda", model: "civic", class: "compact", color: "red" };
\\ or
var car = { color: "red" , manufacturer: "honda", model: "civic", class: "compact" }
```

### Object literals, methods and properties

You can define objects using object-literal notation:
```
var myObj = { 
  color: "orange",
  shape: "sphere",
  type: "food",
  eat: function() { return "yummy" }
};

myObj.eat(); // method
myObj.color; // property
```
