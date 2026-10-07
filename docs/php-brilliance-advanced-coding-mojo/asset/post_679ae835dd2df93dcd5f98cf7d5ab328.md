
Talking points.

```php
if (method_exists($viewData, 'greet')) {
  // not executed.
  $viewData->greet();
}
```

Therefore we have to go back to editing the skeleton class itself in order to support duck typing. We do this by adding a specific method to reliably give us that boolean response that we are looking for.

```php
<?php
class ViewData {
  private $methods = array();
  ...

  public function hasMethod($methodName) {
    return (
      array_key_exists($methodName, $this->methods) &&
      is_callable($this->methods[$methodName])
    );
  }

// Consequently, to duck type
if ($viewData->hasMethod('greet')) {
  $viewData->greet('Joe');
}
```

This is better of course, since it provides us with a little extra safety when handling such an awkward beastie.

# Moving on

Our attention has been concentrated on the finer details and small print for a little too long now. It's time to zoom out a bit, grab ourselves a nice cup of tea and head into Part Three to start picking over patterns, principles and paradigms.

# Brain Check

Welcome to the very last chapter of Part Two.

This is the part where we test ourselves on the material that we’ve covered in this part of the book by asking ourselves, “Could I give a lightning talk on each one of these?”

It's a checklist and a guide for highlighting areas of further reading.

# Interfaces

Interfaces allow us to express a guarantee to an object’s collaborators that the methods described are available in the implementing object. An abstract parent class also provides an interface that we can type-hint on, but in this case the guarantee is not present and the onus is upon the developers to ensure that child classes honour the parent’s interface.

# Namespaces

Namespaces provide us with a means to package our code into cohesive, logical, well organised units or modules and avoid naming clashes with other, third party code that we might bring. The autoloading standards PSR-0 and PSR-4 require name-spacing our code but provide great convenience and compatibility with other packages that follow the same standards.

# Composer

Composer has become the package manager of choice in the world of PHP application development, supplant even Pear by providing both ease of use and extraordinary power when it comes to managing an application’s dependencies.

# Traits

Traits were added to PHP in order to provide a mechanism for code reuse to classes that otherwise bear no relationship to each other. Traits are applied to a consuming class in a system-level copy-and-paste like procedure but care

# Brain Check

should be exercised when using them since not all of a trait's methods will be imported when the consuming class already provides identically named methods.

# Closures

Closures are also known as anonymous functions since they can be declared without a function name. Instead, the function that a closure represents is applied directly to a variable's value. Internally, closures are represented as instances of the Closure class, with the functionality bound to the `__invoke()` magic method to allow them to be treated as callbacks. Both types may be tested for instances of the “callable” type.

# Duck typing

Duck typing is a form of testing a variable's abilities rather than typehinting for a particular Interface or class name. In object oriented, this generally means testing the variable for the presence of specific methods and/or properties before attempting to use those methods or properties.

# Standing on Principles

> “You believe any of this voodoo bullshit, Blair?" - Childs

# Building on bedrock

There. We have successfully navigated the foundational stuff. Don't you feel better for it? I know I do.

Even if the benefits of having done so are not apparent, they should do soon. Irrespective of whether it has been quite time since last considered things like encapsulation and inheritance or not, or even encountered them in a book, what we've actually been doing is getting that bedrock in place. Our goal has been to ensure that we have a solid foundation upon which to build those glittering palaces of software magnificence.

The relevance of the first two parts of this book will become all too apparent within the forthcoming pages. In this part of the book, we step beyond those foundations and start putting into place what will eventually become the subliminal techniques that masters of craft somehow exhibit naturally.

There comes a part in a craftsman's career where conscious thought is no longer required when it comes to applying a hammer blow to the head of a chisel or to the stroke of a brush against canvas. Experience dictates how hard or fast the action should be. When such a craftsman finds himself stopping to gauge the speed, strength, or direction of the action, that's the point where they fluff it.

Here we'll be considering the principles that will guide the software craftsman's hand, with enough repetition to encourage them to become more “muscle memory” than conscious thought.

Over the coming pages we're going to explore the principles, patterns, and paradigms that are necessary for attaining PHP Brilliance. Only the essential ones though. It isn't the intention for this to become a pattern catalogue, not least because there are already plenty of excellent examples readily available for the developer who is interested in such.

Nevertheless, those that are presented here share exceedingly close ties to the material that we have already covered or the material that is yet to come.

In other words, there will be plenty of those circular references that I hinted at at the start of this book.

Let’s get started then.

# Ghostbusters

Remember Joe from Part One? As likeable a chap as he was, we had to let him go. No matter how likeable he was, the company couldn't be seen to be supporting the torrenting of that kind of material frankly. In his place, we have Lizzie. She’s an ace.

However, she got a bit too excited about the possibilities presented in the Closures chapter and decided it would be a good idea to build a DataMapper type of thing that would pull the data out of models and save the changed bits back into the database.

It’s an entirely commendable attitude of course, but it’s also the reason why we’re starting the real content of this part of the book with an anti-pattern. All of that excitement that bubbled up with the closures stuff needs to be put in check somehow.

The anti-pattern in question is called The Poltergeist. It’s also known as the Gypsy Wagon, but I think Poltergeist is the more apt name for it it describes a phenomenon where “something turns up, causes things to happen and disappears again”.

In itself, this is a very apt description of the wrong kind of use that closures can be put to and it manifests itself in objects that have no real substance, objects whose sole apparent purpose is to make things happen and then go away. Our consideration of the poltergeist is doubly important since we spent a good bit of time considering how we might divide the objects into knowers and doers.

The knowers of our system are more appropriately divided into two camps. The first, larger camp is the one that we can label for Entities. These are the key players, the models that curate our application’s data, providing both the properties that retain that data and the methods that allow the data to be manipulated.

The second, much smaller camp of knowers consists of value objects. These are the little blighters that allow us to transport complex structures around the system from one process to the next. Neither operate on the data that they hold nor perform processes because of it.

This leaves us then with the doers. Doers are the critters that we will perform the processes that we ask of, the ones that are more properly known as Services.

Example of poltergeist in action, albeit an exceedingly skinny one. Nevertheless, what we are left with an object has no discernible purpose other than to create a transient bridge between a model's data and the save mechanism.

This in itself provides us with a process that is difficult to trace an error arise but that isn't the issue we need. We would, in fact, be better served by creating a more explicit bridge between the model object and the storage. As we've seen previously, this can be achieved by injecting the model with a data transport object, allowing the model to function properly and with access to the information it requires and still providing the link back to the mapper as we desire.

To take a look at another concept that we've already encountered and consider how it might display poltergeist-like behaviour, think back to when I suggested we remove the `register()` method from the *User* model. We might be tempted to create a single, unifying object whose purpose is to co-ordinate our entire creation process.

We will begin with the kind of code that less experienced developers are prone to writing *â putting the process logic into the body of a controller action.
