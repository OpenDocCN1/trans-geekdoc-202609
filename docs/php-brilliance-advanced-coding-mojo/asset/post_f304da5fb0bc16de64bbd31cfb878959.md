
# The Courier anti-pattern

The Courier anti-pattern crops up whenever an object receives a dependency that it doesn’t use itself. Instead, that dependency was passed to it in order to subsequently pass it on to another of the object’s collaborators. This presents a form of tight coupling in that the intermediary (or courier) implied knowledge of what the final recipient needs in order to function. If those needs change, then it follows that code changes will be required in the courier also, adding fragility to the codebase.

# The Law of Demeter

This isn’t a law is perhaps the most effective principle when it comes to promoting loose-coupling. Also known as the principle of least knowledge, it becomes violated whenever code exhibits awareness of another object’s internal structure. All objects should only be aware of the public interfaces of the other objects that it directly collaborates with. In this way breakages may be avoided when the internal implementation of other objects is changed but the public interface remains the same.

# The Testing Pyramid

An illustrative concept that encourages us to have a broad base of unit testing rising to a narrow pinnacle of functional and manual testing, with layers of other types of testing in between; e.g., integration testing. Anything with a broad base is generally more stable than its narrow based brethren. However, many software projects take the inverse approach and focus on testing the user interface first, leading to something known as the testing ice-cream cone. Ice-cream cones are not generally stable, even when placed on a level surface.

# Moving on to SOLIDS

> “I know you gentlemen have been through a lot, but when you find the time, I’d rather not spend the rest of this winter TIED TO THIS FUCKING COUCH!” - Garry

# Introducing the SOLID principles

Placeholder chapter - content coming soon!

# Placeholders

Is this the end?

Not at all, but some readers have suggested that I include placeholder chapters (essentially empty chapters) in order to provide some way of illustrating the content that is still to come.

Experimentally then, I’ve done just that.

The chapters that follow are empty placeholders that will progressively be filled with content as I work through each release.

Is this a good idea?

Do you find it preferable to see what more there is to come? Or do the empty chapters get annoying if you keep flicking from the table of contents only to find an empty page?

Please do let me know your thoughts:

Thunder

feedback@vanqard.com²²³

In the meantime, you can jump straight to the content at the end of the book by clicking / tapping here

## The Single Responsibility Principle

This is an empty placeholder chapter. Content coming soon!

# The Open / Closed Principle

This is an empty placeholder chapter. Content coming soon!

# The Liskov Substitution Principle

This is an empty placeholder chapter. Content coming soon!

# The Interface Segregation Principle

This is an empty placeholder chapter. Content coming soon!

# The Dependency Inversion Principle

This is an empty placeholder chapter. Content coming soon!

# Talking Points

This is an empty placeholder chapter. Content coming soon!

# Brain Check

Welcome to the very last chapter of Part Four.

Being able to deliver a lightning talk on each of the SOLID principles is especially challenging, but not beyond the realms of possibility for sure.

# Applying Software Architectures

> "I was wonderin' when El Capitan was gonna get a chance to use his popgun." 
Palmer

# Introducing Architectures

This is an empty placeholder chapter. Content coming soon!

## To MVC or not MVC

This is an empty placeholder chapter. Content coming soon!

# Service Oriented Architecture

This is an empty placeholder chapter. Content coming soon!

# API Oriented Architecture

This is an empty placeholder chapter. Content coming soon!

## The Architectural Fortress

This is an empty placeholder chapter. Content coming soon!

# Talking Points

This is an empty placeholder chapter. Content coming soon!

# Brain Check

This is an empty placeholder chapter. Content will be coming soon.

# DON’T PANIC!

Even though we're about to move into “appendices” territory, there is still plenty of the book’s main content still to drop over the coming weeks.

I've established the beginning of the appendix on PHP7 due to its highly topical nature. At this stage we now have an agreed upon list of features that are expected to make it into the final release in October 2015. Not only that, with the nightly builds already available, we have the opportunity to try out and familiarise ourselves with some of the new features before the language changes impact upon our daily coding.

# Appendices

## PHP7

It should be borne in mind that, at the time of writing, PHP7 has only just gone GA, meaning that we are likely to see a flurry of bug reports and bug fix releases in the very near future. That being said, most of the content included here is based on RFCs meshed with my own experiments of using the PHP7 nightly build.

> This appendix is likely to be in a state of great flux. With a new version landing on our desktops, we may have a little time to wait

With due appreciation of that warning above, let's now start to take a look at how some of the changes coming in PHP7 will impact upon the material we've already covered in the first parts.

## Scalar Hinting

This is perhaps one of the most impactful changes to the language that PHP7 brings with it, something that is readily apparent simply by observing the amount of heated debate the topic has generated whilst the RFCs were being proposed, rejected, redrafted and resubmitted.

Why such heated debate? The polarisations from the consideration of whether PHP should be a weakly language or not, and if not how is the typing support to be implemented in a way that causes the least disruption.

## In the blue corner

The proponents for retaining weak typing argue that PHP should continue to honour its historical roots and behave like it has always in the past. This means that it should continue to support well established expectations as being able to send a string that looks like a number to a function strictly numeric values.

```php
<?php

class Calculator
{
    function add($a, $b)
    {
        return $a + $b;
    }
}

$calc = new Calculator();

$first = "12"; // A string
$second = 4.5; // An float

echo $calc->add($first, $second);

// Output: 16.5
```

Even though the first parameter provided is a string variable, internally PHP can handle the type conversion to a float and perform the addition quite readily, Retaining the weakly typed nature of PHP allows the language to follow the principle of least astonishment: It's always worked like this, there's no reason why we need to surprise everybody by breaking their applications when they pass number-like strings to functions strictly numeric values.

This argument is particularly relevant in the context of the application that employs Composer. What would happen if one of the packages that we're importing into our application started declaring method parameter types that we are unprepared for? Bearing in mind that the values in the $_GET and $_POST arrays are always strings, one vendor releasing a strongly typed update to their package could mean that we end up with a lot of refactoring to do just to get our application working again.

How so?

Imagine that the calculator class from the first example was in a package that I provided and that your application depended upon. If I elected to go for a strongly typed implementation, it might end up looking like this.
