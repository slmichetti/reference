## Remove Page Content


.removeChild() - removes a child element; requires:
* a parent element
* the child element that will be removed
```
<parent-element>.removeChild(<child-to-remove>);
```

**Steps:**
* find the item and its parent in a variable
* store the parent in a variable
* verify what is the firstElementChild to find the element you want to remove
* store in a variable
* remove the child from its parent
* result = removed from the page and the DOM

**Shortcut**
The removeChild() method does require access to parent to function
Every element has a parentElement property that refers to its parent. You can use the parentElement property to move focus to the element's parent. Then call the remove or append child on taht referenced parent element

Example:
```
const mainHeading = document.querySelector('h1');
```

Selects the first h1 on the page and stores it in the mainHeading variable.

```
mainHeading.parentElement.removeChild(mainHeading);
```

Starts with the mainHeading variable, calls .parentElement, so the focus of the next code is directed at the parent element. Then .removeChild() is also called on the parent element. Finally, mainHeading is passed as the element that needs to be removed from its parent. 
**An element uses itself to remove itself from the parent**


* .remove()
There is an easier and faster way to remove a child element. This method can be called directly on the element to delete.
```
const mainHeading = document.querySelector('h1');

mainHeading.remove();
```

Other helpful properties:
* .firstChild
* .firstElementChild
* .parentElement

The difference between .firstChild and .firstElementChild, is that .firstElementChild will always return the first element, while .firstChild might return whitespace (if there is any) to preserve the formatting of the underlying HTML source code.

### Style Page Content

* .style.<property>
* .cssText()
* .setAttribute()
* .className
* .classList

**CSS Specificity**

The means by which browswers decide which CSS property values are the most relevant to an element and, therefore, will be applied. 

* Least specific: rules in a stylesheet
* More specific:  rules in a <style> tag
* Most specific: rules in a tag's <style> attribute

The closer the style rule is to an element, the more specific it is. 
	i.e. a rule in a style attribute on an element will override a style rule for that element in a CSS stylesheet. There is also the specificity of the type of selector being used. An _ID_ is more specific than a class.

### Modifying an Element's Style Attribute

The most specific rules that you can write for an element are written in that element's style attribute. Acces an element's style attribute using the .style property. Using the .style property, you can only modify one CSS style at a time. 
```
const mainHeading = document.querySelector('h1');

mainHeading.style.color = 'red';
```

### Adding Multiple Styles at Once

 the .style.<property> syntax will let us change just one piece of styling for an element. So the .style.property syntax is perfect for setting one style at a time, but it's not great for controlling multiple styles.

 Use the .style.cssText property to set multiple CSS styles at once!
 ```
 const mainHeading = document.querySelector('h1');

mainHeading.style.cssText = 'color: blue; background-color: orange; font-size: 3.5em';
```

**Notice that when using the .style.cssText property, you write the CSS styles just as you would in a stylesheet; so you write font-size rather than fontSize. This is different than using the individual .style.<property> way.**

**Quiz**
For the element below, which of the following styles will be applied after running this code?
```
<p id="quizzing-quizzes" style="color: orange;">Howdy</p>
```

Width only. 
Only the width styling will be in the element's style attribute. The .style.cssText will overwrite anything that's already in the .style attribute (which removes the color styling). The textDecoration rule is misspelled and should be text-decoration, so it gets dropped.

### Setting an Element's Attributes

Another way to set styles for an element is to bypass the .style.<property> and .style.cssText properties altogether and use the .setAttribute() method:
```
const mainHeading = document.querySelector('h1');

mainHeading.setAttribute('style', 'color: blue; background-color: orange; font-size: 3.5em;');
```

https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style

**.setAttribute() Is Not Just For Styling**
The setAttribute() method is not just for styling page elements. You can use this method to set any attribute for an element. 
```    
const mainHeading = document.querySelector('h1');

// add an ID to the heading's sibling element mainHeading.nextElementSibling.setAttribute('id', 'heading-sibling');

mainHeading.nextElementSibling.style.backgroundColor = 'red';

```

### Accessing an Element's Classes

HTML - HTML file
CSS - styling in the style sheet
interactivity - in javascript file

They do have to be tied together a little, but best practice is to keep them separate.

**.className Property**
This property returns a string of all of the element's clases. If an element has the following HTML:
```
<h1 id="main-heading" class="ank-student jpk-modal">Learn Web Development at Udacity</h1>
```
use .className to access the list of classes:
```
const mainHeading = document.querySelector('#main-heading');

// store the list of classes in a variable
const listOfClasses = mainHeading.className;

// logs out the string "ank-student jpk-modal"
console.log(listOfClasses);
```
The .className property returns a space-separated string of the classes. This isn't the most ideal format, unfortunately. We can, however, convert this space-separated string into an array using the JavaScript string method, .split():
```
const arrayOfClasses = listOfClasses.split(' ');

// logs out the array of strings ["ank-student", "jpk-modal"]
console.log(arrayOfClasses);
```

Now that we have an array of classes, we can do any data-intensive calculations:
* use a for loop to loop through the list of class names
* use .push() to add an item to the list
* use .pop() to remove an item from the list

.className is a property, so we can set its value just by assigning a string to the property:
```
mainHeading.className = "im-the-new-class";
```
**The above code erases any classes that were originally in the element's class attribute and replaces it with the single class im-the-new-class.**

### .classList Property

Returns a DOMTOkenList
```
<h1 id="main-heading" class="ank-student jpk-modal">Learn Web Development at Udacity</h1>

const mainHeading = document.querySelector('#main-heading');

// store the list of classes in a variable
const listOfClasses = mainHeading.classList;

// logs out ["ank-student", "jpk-modal"]
console.log(listOfClasses);
```

https://developer.mozilla.org/en-US/docs/Web/API/Element/classList

The .classList property has a number of properties of its own. Some of the most popularly used ones are:

* .add() - to add a class to the list
* .remove() - to remove a class from the list
* .toggle() - to add the class if it doesn't exists or remove it from the list if it does already exist
	* If you try to toggle a nonexistent class, it is added to the list of classes
* .contains() - returns returns a boolean based on if the class exists in the list or not


**Use this .classList frequently!**
.classList is by far the most helpful property of the bunch, and it helps to keep your CSS styling out of your JavaScript code.

