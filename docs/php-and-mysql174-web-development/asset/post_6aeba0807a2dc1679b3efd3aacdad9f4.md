
## Chapter 23 Integrating JavaScript and PHP

This is only the most basic of introductions to jQuery but should be sufficient to introduce you to jQuery as you continue on the AJAX-related examples of this chapter. Please consult the jQuery documentation on selectors for an in-depth understanding of the full syntax of selectors and their function: https://learn.jquery.com/using-jquery-core/selecting-elements/

## Acting on Sets

Now that you have an idea of how to search through an HTML document for specific elements, let's discuss the various ways you can act on a selector. jQuery selectors are plural in nature, meaning a selector with a single element is considered a set of one rather than a single element. Thus, you can perform actions on the whole regardless of whether it is one or hundred individual elements in that set.

Consider the jQuery .val() method which allows the developer to get or set the value of an input element:

```
var myInput = '#first-name';
console.log('The value of the input element with #first_name is: ' + myInput.val());
myInput.val('John');
console.log('The value of #first_name has been changed to: ' + myInput.val());
```

In this example we are selecting a single HTML element by the ID of that element, which in this case is first-name. However, because the selector always returns a set of elements the same method could have been used. To make this a little more practical, let's introduce a second jQuery method addClass(), as its name implies, adds a new class to HTML elements:

```
var nameFields = $('.name');
nameFields.addClass('form-control');
```

This example finds all HTML elements that have the existing class, and applies a new class to them called form-control.

In more complicated cases, where elements may or not already exist, it becomes important to determine if a selector actually returned any elements when executed. Since a set of zero is technically a set (and thus return a boolean true in JavaScript), you must use the length property of the set to determine if anything is actually in it:

```
var nameFields = $('.name');

if (nameFields.length > 0) {
    console.log('We found some elements with the 'name' class');
} else {
    console.log('We found zero elements with the 'name' class');
}
```

## Introduction to jQuery Events

Events are a critical part of JavaScript, and by extension, of jQuery. Since JavaScript itself is an asynchronous programming language (meaning the logic of the program does not necessarily execute in the same order every), events are critical to ensuring your application is not lost when the order changes.

There are countless events available to the jQuery developer all sorts sorts of various circumstances. Some of these events are native to JavaScript itself, such as the click event broadcast every time a user clicks on something. Other events are constructs of jQuery, such as the ready event that is fired when all the resources for a given HTML document have properly loaded.

In the hierarchy of an HTML document, events bubble up from their source HTML element through the parent elements and eventually through the entire document, triggering actions for listening to them. Typically in jQuery, a selector can have a event listener. The selector is first used to identify the relevant HTML elements in question and then the on() method is used to listen for and perform logic when that event is triggered. One of the simplest versions of this listening is the ready event, triggered by jQuery upon full loading of the HTML document and its resources:

```
$(document).on('ready', function(event) {
  // Code to execute when the document is ready
})
```

Like most jQuery, the on() method can be used on any given selector. For example, if you wanted to respond every time a user clicked on a link you could attach a listener on all <a> tags with an href attribute and listen for the click event:

```
$('a').on('click', function(event) {
  // Do something every time an <a> HTML element is clicked
})
```

The on() method is a universal way to bind a listener to an event, but for convenience and historical reasons, jQuery also provides a number of methods mapping directly to the event name. For example, $(document).on('ready', ...) and $(document).ready(...) are identical in function.

Depending on the nature of your original selector, you might find yourself createating a single event for a set of many HTML elements, but when fired only on the specific element that triggered the event. You will note in the two examples the closure to handle the event accepted a single parameter event. This event parameter is the event object created when the event fired, and within its target property the specific element that fired this specific event. Thus, if you wanted to attach a specific button when clicked you could do as follows:

```
$('button').on('click', function(event) {
  var button = $(event.target);

  // Do something with the specific button that was clicked
})
```

## Chapter 23 Integrating JavaScript and PHP

Likewise, especially for certain events like the click of an <a> HTML element, the default listener of the event may take actions you don't want to occur. For example, consider the following code:

```
$('a').on('click', function(event) {
  var link = $(event.target).attr('href');
  console.log("The link clicked a URL of: " + link);
});
```

Logically speaking, you could use this snippet of code to listen for a click event, extract the href attribute from the source of that click event, and then display the value of that attribute in the browser's console. You would be right, however, if the selector always returns a set of elements the same method could have been used. To make this a little more practical, let's introduce a second jQuery method addClass(), as its name implies, adds a new class to HTML elements:

### Table 23.1 Useful jQuery Events

| Event | Type | Description |
| :--- | :--- | :--- |
| change | Form Event | Triggered when a form element changes |
| click | Mouse Event | Triggered when a given element is clicked |
| dclick | Mouse Event | Triggered when given element is double-clicked |
| error | JavaScript Event | Triggered when a JavaScript error occurs |
| focus | Form Event | Triggered when a form element receives focus, prior to actually focused |
| focus | Form Event | Triggered when a form element is focused |
| focusout | Form Event | Triggered when a form element loses focus |
| hover | Mouse Event | Triggered when the mouse floats over given element |
| keydown | Keyboard Event | Triggered when a key is pressed |
| keypress | Keyboard Event | Triggered when a key is pressed and released |
| keyup | Keyboard Event | Triggered when a key is released |
| ready | Document Event | Triggered when the document model is fully loaded |
| submit | Form Event | Triggered when a given form is submitted |

Pulling all the information presented so far in this chapter regarding selectors and events, let's revisit a revamped version of the document example in Listing 23.1 to include the use of events to perform various actions. This new document is shown in Listing 23.2.
