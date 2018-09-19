## Update Existing Page Content

### Inner HTML

Every element inherits properties and methods from the Element Interface (remember this from the previous lesson!). This means that every element has an .innerHTML property. This property, as it's rightly named, represents the markup of the element's content. We can use this property to:

get an element's (and all of its descendants!) HTML content
set an element's HTML content


The .innerHTML property sets or returns the HTML content inside the selected element (i.e. between the tags).

There's also the rarely used .outerHTML property. .outerHTML represents the HTML element itself, as well as its children.

**An Element's Text Content**
So .innerHTML will get/set an element's HTML content. If we just want the text content, we can use the fantastically named .textContent property!

The .textContent property will:

* set the text content of an element and all its descendants
* return the text content of an element and all its descendants

Set an element's text content just like any other property
```
nanodegreeCard.textContent = "I will be the updated text for the nanodegreeCard element!";
```

Passing any text that looks like HTML to the .textContent property will still be displayed as text. It will not be displayed as HTML when the element is rendered.

**To update an element, including its HTML, then you need to use the .innerHTML property:**
```
myElement.innerHTML = 'The <strong>Greatest</strong> Ice Cream Flavors';  // works as expected
```

### .innerText property

The .innerText property can be used to get/set an element's text content, but there are some differences between the two properties

.textContent sets/gets the text content of an element. Returns all of the text, regardles of CSS.

.innerText returns text as it will be seen visually. If CSS is used to hide any text inside that element, .innerText will not return that text, while .textContent will return it. .innerText will also honor changes to things like capitalization.

**Use .textContent** since that will return all of the text no matter what. Rarely will you actually want only the visible text.

The difference between .textContent and .innerText. .textContent completely ignores any CSS styling and returns all of the element's HTML just as it's listed in the HTML. On the other hand, the .innerText property will take CSS styling into consideration and will return the text that is visibly rendered on the page.

## New Page Content

**.createElement()** https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement
* The .createElement() method is a method on the document object.

* document.createElement('p'); == creates a new paragraph element

// creates and returns a <span> element
* document.createElement('span');

// creates and returns an <h3> element
* document.createElement('h3');


**.createTextNode()**
* creates a paragraph element
* creates a text node
* appends the text node to the paragraph
* appends the paragraph to the tag

```
const myPara = document.createElement('p');
myPara.textContent = 'I am the text for the paragraph!'; document.body.appendChild(myPara);
```
Therefore, instead of creating a new text node and appending it to an element, it's faster and easier to just update the element's text with the .textContent property.

**.appendChild()** used to add an element to the page. 
The .appendChild() method is called on one element, and is passed the element to append. The element that is about about to be appended is added as the last child. 

To use the .appendChild() method, it needs to be called on another element, not the document object!
```
// create a brand new <span> element
const newSpan = document.createElement('span');

// select the first (main) heading of the page
const mainHeading = document.querySelector('h1');

// add the the <span> element as the last child element of the main heading
mainHeading.appendChild(newSpan);
```
The .appendChild() method will move an element from its current position to the new position.


.insertAdjacentHTML()

Adding Content To The Page
You may have noticed that using document.createElement() to create an element didn't actually add that newly created element anywhere on the page! Creating an element...just creates it. It doesn't add it to the DOM. Since the element isn't added to the DOM, it doesn't appear in the page 

### Inserting HTML In Other Locations

By definition, the .appendChild() method will add an element as the last child of the parent element.

The .insertAdjacentHTML() method! The .insertAdjacentHTML() method has to be called with two arguments:

* the location of the HTML
* the HTML text that is going to be inserted

The first argument to this method will let us insert the new HTML in one of four different locations

beforebegin – inserts the HTML text as a previous sibling afterbegin – inserts the HTML text as the first child beforeend – inserts the HTML text as the last child afterend – inserts the HTML text as a following sibling
```
<!-- beforebegin -->
<p>

    <!-- afterbegin -->
    Existing text/HTML content
    <!-- beforeend -->
</p>
<!-- afterend -->
```

**Here's how we'd call .insertAdjacentHTML():**
```
const mainHeading = document.querySelector('#main-heading');
const htmlTextToAdd = '<h2>Skydiving is fun!</h2>';

mainHeading.insertAdjacentHTML('afterend', htmlTextToAdd);
```

**.insertAdjacentHTML**
https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML
This method needs to be called on a parent element
Also needs to be called w/ two aguments - the position and the text (must be text, not html)

**Recap of adding new page content**
create new DOM elements and add them to the page. We looked at the following methods:

* .createElement() to create new elements
* .appendChild() to add a child element to a parent element as its last child
* .createTextNode() to create a text node
* .insertAdjacentHTML() to put HTML text anywhere around an element

Some important things to note are:

* if an element already exists in the DOM and this element is passed to .appendChild(), the `.appendChild() method will move it rather than duplicating it
* an element's .textContent property is used more often than creating a text node with the .createTextNode() method
* the .insertAdjacentHTML() method's second argument has to be text, you can't pass an element


