## Document Object Model

### Document Object Model (DOM)

The DOM stands for "Document Object Model" and is a tree-like structure that is a representation of the HTML document, the relationship between elements, and contains the content and properties of the elements. 
The objects contain all of the properties - its the full parsed representation of the HTML markup.

* HTML is received
* HTML tags are converted to tokens
* Tokens are converted to nodes
* Nodes are converted to the DOM


**To reiterate the process, it's:**

* characters
* tags
* tokens
* nodes
* DOM

When you request a website, it responds with HTML. The browser receives a stream of HTML. The bytes are run through a parsing process that determines the different characters (e.g. the start tag character <, an attribute like an href, a closing angle bracket >). After parsing has occurred, a process called tokenization occurs. This takes one character at a time and builds up tokens. 
The tokens are:
* DOCTYPE
* start tag
* end tag
* comment
* character
* end-of-life

The output of this is a tree-like structure - the DOM.

A JavaScript object is a tree-like structure that has properties and values. So the DOM can be accessed using a special object provided by the browser: document

DevTools Console
Type document
The document object is provided by the browser and is a representation of the HTML document. 
The docuent object is not part of JavaScript, but it is expected to already exist and be freely accessible to JavaScript code.

The DOM is not part of the JavaScript language

It is constructed from the browser and is globally accessible by JavaScript code using the document object

### Select An Element by ID

Gaining access to specific elements using their ID attribute through JavaScript and the DOM

The **document object** is an object, just like a JavaScript object - meaning it has key/value pairs. Some of the values are just pieces of data, while others are functions (methods) that provide some type of functionality. 

### DOM METHODS

#### .getElementByID()
```
document.getElementById('ID');
```
This method must have a string passed of the ID of the element that you want to find and get returned. 
```
document.getElementById('footer');
```
You dont need to use the #footer b/c it knows its search for an ID

**Store elements as variables**
* Find element using document.getElementbyId('logo');
* Create a variable to store the element 
* const mainLogo - document.getElementbyId('logo');
* Access the element later by using the variable name (mainLogo)

**Recap**
There are a couple of important things to keep in mind about this method:
* it is called on the document object
* it returns a single item

```
// select the element with the ID "callout"
document.getElementById('callout');
```

### Select Multiple Elements at Once

Since IDs are unique, and since there will be only one element in the HTML with that ID, document.getElementById() will only ever return at most one element. 

#### .getElementsByClassName()
Accessing Elements By Their Class with a string you want to search for/return
```
document.getElementsByClassName();
```

Right click to inspect and see what the elements class is, then search for that class using this method.

.getElementsByClassName() returns an array-like data structure of elements. (Ex of 'line-numbers' returns an HTML collection (not an array)

#### .getElementsByTagName()

```
document.getElementsByTagName('p');
```

When the results are returned, you can right click on one, reveal in elements pane, then from elements right click to scroll into view to view it in the web page

**Recap**
Two ways to select multiple DOM elements:

* .getElementsByClassName()
* .getElementsByTagName()

There are a few important things to keep in mind about these two methods:

* both methods use the document object
* both return multiple items
* the list that's returned is not an array


## Nodes, Elements and Intefaces

### Node 

In object-oriented programming: 
**Node = Class** - the blueprint for a building; can have the data about the buildig (properties) and the capabilities (methods/functionality)
Its the **Interface** with the properties and methods for real nodes (the individual items) 
	"interface" is a technical, computer science word for a list of properties and methods that are inherited.

**Definitions**
* interface = blueprint
* properties = data
* methods = functionality

node = object
the real objects built from the blueprint

the Node Interface is a blueprint for all of the properties (data) and methods (functionality) that every real node has after it's been created. Now, the Node Interface has a lot of properties and methods, but it's not very specific

### Element Interface

Element interface is a blueprint for creating elements. Contains a list of all the properties and methods available to an element. 

**And it is a descendent of the Node Interface**
	Elment points to the parent, Node.

Since Element is pointing at Node, this indicates that the Element Interface inherits all of the Node Interface's properties and methods. 
	Any element that was created from teh Element interface is also a descendent from the Node Interface, so it is also a node.

**Using $0 in the developer tools console refers to the highlighted element**

The Element Interface inherits from the Node Interface, not the Document Interface (yep, there's a Document Interface!). The Element Interface has its own .getElementsByClassName() that does the exact same thing as the one on the document object.

This means that you can use the document object to select an element, then you can call .getElementsByClassName() on that element to receive a list of elements with the class name that are descendents of that specific element!
```
`js // selects the DOM element with an ID of "sidebar" const sidebarElement = document.getElementById('sidebar');

// searches within the "sidebar" element for any elements with a class of "sub-heading" const subHeadingList = sidebarElement.getElementsByClassName('sub-heading'); `
```

**.outerHTML property**
The outerHTML attribute of the Element DOM interface gets the serialized HTML fragment describing the element including its descendants. It can also be set to replace the element with nodes parsed from the given string.

**.id property**
Element.id
Is a DOMString representing the id of the element.

**.textContent property**
Node.textContent
Returns / Sets the textual content of an element and all its descendants.


### HTML Element
https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement
The HTMLElement interface represents any HTML element. 
Inherits from Element and Node.

### More Ways to Access Elements

Not all browsers support every standard. They do now, for these three methods, but there are hundreds of other methods with varying levels of support.

That's why almost every method on MDN has a Browser compatibility table that lists when each browser started supporting that specific method.


### jQuery

Historically was used to evaluate the code for different browsers. 

Been replaced by native DOM methods.


```
#header {
    color: 'red';
}

.header {
    color: 'red';
}

header {
    color: 'red';
}
```

Each one of these sets the color to read, but the difference is the selector - selecting by ID, class and tag.

#### querySelector Method

We can use the .querySelector() method to select elements just like we do with CSS. We use the .querySelector() method and pass it a string that's just like a CSS selector:

```
// find and return the element with an ID of "header"
document.querySelector('#header');

// find and return the first element with the class "header"
document.querySelector('.header');

// find and return the first <header> element
document.querySelector('header');
```

**.querySelector() returns a single element**
However, even though .getElementsByClassName() and .getElementsByTagName() both return a list of multiple elements, using .querySelector() with a class selector or a tag selector will still only return the first item it finds.


#### querySelectorAll Method

The .querySelector() method returns only one element from the DOM (if it exists). For times you want to get a list of all elements with a certain class or all of one type of element (e.g. all <tr> tags), use the .querySelectorAll() method
```
/ find and return a list of elements with the class "header"
document.querySelectorAll('.header');

// find and return a list of <header> elements
document.querySelectorAll('header');
```

Practice Example:

in dev tools console

document.querySelectorAll('h2')
//store in a variable
const listOfElements = document.querySelectorAll('h2');
//loop over each item of the list with a for loop
for(let i = 0; i < listOfElements.length; i++) {
	console.log('i is ' + i);
	console.log(listofElements[i]);
}

prints a numbered list of the h2 items 

```
const allHeaders = document.querySelectorAll('header');

for(let i = 0; i < allHeaders.length; i++){
    console.dir(allHeaders[i]);
}
```

