## Working with Browser Events

### monitorEvents() method

Instructs the DevTools to log information on the specified targets. 

The first parameter is the object to monitor. All events return if the second parameter is not provided. To specify the events to listen to, pass either a string or an array of strings as the second parameter.

Ex: Listen to click events on the body of the page:
```
monitorEvents(document.body, "click");
```

**monitorEvents documenttion** (https://developers.google.com/web/tools/chrome-devtools/console/events#monitor_events)

The monitorEvents function will keep spitting out all of the events that are happening on the targeted element until the end of time...that, or until you refresh the page. Alternatively, the Chrome browser does offer an unmonitorEvents() function that will turn off the announcing of events for the targeted element:
```
// start displaying all events on the document object
monitorEvents(document);

// turn off the displaying of all events on the document object.
unmonitorEvents(document);
```
One last little bit of info on monitorEvents is that this is for development/testing purposes only. It's not supposed to be used for production code.

### An Event Target

The Node Interface inherits from the EventTarget Interface. Its at the top of the chain. This means that it does not inherit any properties or methods from any other interfaces.  However, every other interface inherits from it and therefore contain its properties and methods. This means that each of the following is an "event target";

* the document object
* a paragraph element
* a video element
* etc.

**The EventTarget Interface is inherited by all nodes and elements. Both the document object and any DOM element can be an event target**

The EventTarget is an interface implemented by objects that can receive events and may have listeners for them. Element, document, and window are the most common event targets, but other objects can be event targets too

Look at the EventTarget Interface - it doesn't have any properties and only three methods! These methods are:

* .addEventListener()
* .removeEventListener()
* .dispatchEvent()

### Adding an Event Listener

.addEventListener() method will let us listen for events and respond to them! (listen means listen for an event, listen to an event, hook into an event, respond to an event.)

An event listener needs three things:
1. an event target - this is called the **target**
2. the type of event to listen for - this is called the **type**
3. a function to run when the event occurs - this is called the **listener**

```
<event-target>.addEventListener(<event-to-listen-for>, <function-to-run-when-an-event-happens>);
```
The <event-target> (i.e. the target) goes right back to what we just looked at: everything on the web is an event target (e.g. the document object, a <p> element, etc.).

The <event-to-listen-for> (i.e. the type) is the event we want to respond to. It could be a click, a double click, the pressing of a key on the keyboard, the scrolling of the mouse wheel, the submitting of a form...the list goes on!

The <function-to-run-when-an-event-happens> (i.e. the listener) is a function to run when the event actually occurs.

ex:
```
const mainHeading = document.querySelector('h1');

mainHeading.addEventListener('click', function () {
  console.log('The heading was clicked!');
});
```
**break down**
* target = the first <h1> element on the page
* event type to listen for is a "click" event
* the listener is a function that logs "The heading was clicked!" to the console

**Quiz**
addEventListener on a site

document.addEventListener('click', function () {
	console.log('the page was clicked');
})


**List of Events that are available**
https://developer.mozilla.org/en-US/docs/Web/Events

Form Events submit


#### Object Equality

Object equality, which includes objects, arrays, and functions. Equality is a common task in most programming languages, but in JavaScript, it can be a little bit tricky because JavaScript does this thing called type coercion where it will try to convert the items being compared into the same type. (e.g. string, number,). 

JavaScript has the double equality (==) operator that will allow type coercion. It also has the triple equality (===) symbol that will prevent type coercion when comparing.

The same information does not correlate to equality
```
{ name: 'Richard' } === { name: 'Richard' }
```

```
var a = {
    myFunction: function quiz() { console.log('hi'); }
};
var b = {
    myFunction: function quiz() { console.log('hi'); }
};
```
Both of these have equality test results of false

```
function quiz() { ... }

var a = {
    myFunction: quiz
};
var b = {
    myFunction: quiz
}
```
This results to True b/c both functions are referring to the same exact quiz function.


**When thinking about equality - think about: Are they Two separate objects or are they different names referring to the same object?**


### Remove an Event Listener

To remove an event listener, we use the .removeEventListener() method. 

the .removeEventListener() method **requires you to pass the same exact listener function to it as the one you passed to .addEventListener().**

pseudo code for remove:
<event-target>.removeEventListener(<event-to-listen-for>, <function-to-remove>);

An event listener needs three things:
1. target - the event target
2. type - the type of event to listen for
3. listener - the function to remove

Process:
```
function myEventListeningFunction() {
    console.log('howdy');
}

// adds a listener for clicks, to run the `myEventListeningFunction` function
document.addEventListener('click', myEventListeningFunction);

// immediately removes the click listener that should run the `myEventListeningFunction` function
document.removeEventListener('click', myEventListeningFunction);
```

FAILED PROCESS
example that would not work (it does not remove the event listener):
```
// adds a listener for clicks, to run the `myEventListeningFunction` function
document.addEventListener('click', function myEventListeningFunction() {
    console.log('howdy');
});

// immediately removes the click listener that should run the `myEventListeningFunction` function
document.removeEventListener('click', function myEventListeningFunction() {
    console.log('howdy');
});
```

This code does not successfully remove the event listener. Again, why does this not work?

* both .addEventListener() and .removeEventListener have the same target
* both .addEventListener() and .removeEventListener have the same type
* .addEventListener() and .removeEventListener have their own distinct listener functions...they do not refer to the exact same function (this is the reason the event listener removal fails!)

Quiz:
Assuming that myForm is a <form> element, will the <form> element have a submit event listener after running the following code, or not?
```
myForm.addEventListener('submit', function respondToSubmit(){...});
myForm.removeEventListener('submit', function respondToSubmit(){...});
```

Since both .addEventListener() and .removeEventListener provide their own respondToSubmit() function and do not refer to the same function, the event listener removal fails, and the <form> will still have an event listener attached to it.

Dev tools "Event Listeners" tab
Will show you all the registered event listeners for the selected item
Click "ancestors" to the element and can see what listeners are there
There is a remove button that removes the listener just for that session

Will also let you see where the function is designed that actually runs
Right click to "show function definition" takes you to the sources pane and shows you where the function was defined (app.js)


### Event Phases

There are three different phases during the lifecycle of an event.
* capturing phase
* at target phase
* bubbling phase

They follow the above order.  First its capturing, then at target, then the bubbling.

Most event handlers run durig the **at target** phase. 

By default, if you click on a child item and a handler doesn't intercept the click, the event will "bubble" upward to the parent, and keep bubbling until something handles it or it hits the document.

Capturing, on the other hand, lets the parent intercept an event before it reaches a child.

Phases of an Event:

Clicking on an event starts the whole process
* Capturing - starts at the tope (Html element) and works its way down)
* at target - Once it reaches the element that was clicked, it switches to the at targe phase
* then switches to the bubbling phase and works its way back up

Up until this point, we've only seen the .addEventListener() method called with two arguments, the:

* event type
* and the listener
```
document.addEventListener('click', function () {
   console.log('The document was clicked');
});
```

There is a third argument to the .addEventListener() method; the useCapture argument. 
**By default, when .addEventListener() is called with only two arguments, the method defaults to using the bubbling phase.**

in this code, .addEventListener() is called with three arguments with the third argument being true (meaning it should invoke the listener earlier, during the capturing phase!).
```
document.addEventListener('click', function () {
   console.log('The document was clicked');
}, true);
```

### Event Handler Setup for the different phases

If you set up  listener to run during the capturing phase, it will bypass any methods tht are set up for the bubbling phase, running first then the event set true to run in capturing, then it will continue to work down through the code, when it switches to bubbling, it will work its way back up the code and run the listener functions in order on its way back to the top.

```
const items = document.querySelector('.quizzing-quizzes');
const el = items[1];

el.addEventListener('click', function () {
    console.log('You clicked on the 2nd quizzing-quizzes item!');
}, false);
```
Set to false means it will run during the bubbling phase

QUIZ

Which message displays first/second to this code:
```
document.addEventListener('click', function () {
   console.log('The document was clicked');
});

document.body.addEventListener('click', function () {
    console.log('The body element was clicked');
});
```

First: The body element was clicked
Second: The document was clicked

### The Event Object

When an event occurs, the browser includes an **event object**.  This is a JavaScript object that includes a lot of information about the event itself. 

The .addEventListener()'s listener function receives (According to MDN):

	a notification (an object that implements the Event interface) when an event of the specified type occurs

Add a parameter so you can store the information that it receives
```
document.addEventListener('click', function (event) {  // ← the `event` parameter is new!
   console.log('The document was clicked');
});
```

The MDN will have all the details regarding the event being logged, including all the data thats being collected.

Without an event object, you are stuck with the default actions. The event object has a .preventDefault() method that a handler call call to prevent the default action from occuring.
```
const links = document.querySelectorAll('a');
const thirdLink = links[2];

thirdLink.addEventListener('click', function (event) {
    event.preventDefault();
    console.log("Look, ma! We didn't navigate to a new page!");
});
```

### Refactoring the number of Event Listeners

By minimizing how many event listeners you have (that do the same thing -- ex. of 200 paragraphs w/ their own listener events and instead adding it to a div), you lose access to the individual items in that div.
```
const myCustomDiv = document.createElement('div');

function respondToTheClick() {
    console.log('A paragraph was clicked.');
}

for (let i = 1; i <= 200; i++) {
    const newElement = document.createElement('p');
    newElement.textContent = 'This is paragraph number ' + i;

    myCustomDiv.appendChild(newElement);
}

myCustomDiv.addEventListener('click', respondToTheClick);

document.body.appendChild(myCustomDiv);
```

### Event Delegation
Event Delegation is the process of delegating to a parent element the ability to manage events for child elements. We were able to do this by making use of:

* the event object and its .target property
* the different phases of an event

The event object has a .target property. This property references the target of the event. 
Let's say that you click on a paragraph element. Here's roughly the process that happens:

* a paragraph element is clicked
* the event goes through the capturing phase
* it reaches the target
* it switches to the bubbling phase and starts going up the DOM tree
* when it hits the <div> element, it runs the listener function
* inside the listener function, event.target is the element that was clicked

event.target gives direct access to the paragraph element that was clicked. Because we have access to the element directly, we can access its .textContent, modify its styles, update the classes it has, etc.
```
const myCustomDiv = document.createElement('div');

function respondToTheClick(evt) {
    console.log('A paragraph was clicked: ' + evt.target.textContent);
}

for (let i = 1; i <= 200; i++) {
    const newElement = document.createElement('p');
    newElement.textContent = 'This is paragraph number ' + i;

    myCustomDiv.appendChild(newElement);
}

document.body.appendChild(myCustomDiv);

myCustomDiv.addEventListener('click', respondToTheClick);
```

### Checking the Node Type in Event Delegation

The listener function logs a message saying that a paragraph element was clicked (and then the text of the target element). This works perfectly! However, there is nothing to ensure that it was actually a <p> tag that was clicked before running that message. In this snippet, the <p> tags were direct children of the <div> element

```
document.querySelector('#content').addEventListener('click', function (evt) {
    if (evt.target.nodeName === 'SPAN') {  // ← verifies target is desired element
        console.log('A span was clicked with text ' + evt.target.textContent);
    }
});
```

every element inherits properties from the Node Interface. One of the properties of the Node Interface that is inherited is .nodeName. We can use this property to verify that the target element is actually the element we're looking for. When a <span> element is clicked, it will have a .nodeName property of "SPAN", so the check will pass and the message will be logged. However, if a <p> element is clicked, it will have a .nodeName property of "P", so the check will fail and the message will not be logged.

**The nodeName's Capitalization**
The .nodeName property will return a capital string, not a lowercase one. So when you perform your check make sure to either:

* check for capital letters
* convert the .nodeName to lowercase
```
// check using capital letters if (evt.target.nodeName === 'SPAN') { console.log('A span was clicked with text ' + evt.target.textContent); }

// convert nodeName to lowercase if (evt.target.nodeName.toLowerCase() === 'span') { console.log('A span was clicked with text ' + evt.target.textContent); } 
```

### Incremental DOM

Key Item: When the HTML is received and converted into tokens and built into the document object model is a sequential process. When the parser gets to a <scipt> tag, it must wait to download the script ile and execute that JavaScript code. **This is why the placement of the JavaScript file matters!**

if the DOM is built sequentially, _if_ the JavaScript code is moved to the very bottom of the page, then by the time the JavaScript code is run, all DOM elements will already exist!

Or an alternative solution is to use browser events.

#### The Content is Loaded Event

When the document object model has been fully loaded, the browser will fire an event. This event is called the DOMContentLoaded event, and we can listen for it the same way we listen to any other events:
```
document.addEventListener('DOMContentLoaded', function () {
    console.log('the DOM is ready to be interacted with!');
});
```

There are indicators in the DevTools, Network pane that indicate when the DOM is loaded
The target of the DOMContentLoaded event is the document object.

Because we now know about the DOMContentLoaded event, we can use it to keep our JS code in the <head>
```
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="/css/styles.css" />
    <script>
      document.addEventListener('DOMContentLoaded', function () {
          document.querySelector('footer').style.backgroundColor = 'purple';
      });
    </script>
    ```

We have the JavaScript code in the <head> element, but it is now wrapped in an event listener for the DOMContentLoaded event. This will prevent the DOM-styling code from running when the browser gets to it. Then, when the DOM has been constructed, the event will fire and this code will run.

If you're looking at somebody else's code, you may see that their code listens for the load event being used instead (e.g. document.onload(...)). load fires later than DOMContentLoaded -- load waits until all of the images, stylesheets, etc. have been loaded (everything referenced by the HTML.) Many older developers use load in place of DOMContentLoaded as the latter wasn't supported by the very earliest browsers. But if you need to detect when your code can run, DOMContentLoaded is generally the better choice.

However, just because you can use the DOMContentLoaded event to write JavaScript code in the <head> that doesn't mean you should do this. Doing it this way, we have to write more code (all of the event listening stuff) and more code is usually not always the best way to do something. Instead, it would be better to move the code to the bottom of the HTML file just before the closing </body> tag.
	when would you want to use this technique? Well, JavaScript code in the <head> will run before JavaScript code in the <body>, so if you do have JavaScript code that needs to run as soon as possible, then you could put that code in the <head> and wrap it in a DOMContentLoaded event listener. This way it will run as early as possible, but not too early that the DOM isn't ready for it.




