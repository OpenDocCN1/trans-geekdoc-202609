
Progressive progression, objectively.

have been around. Some of the core concepts are not subject to the short shelf lives of the last or the current or the next big thing. Sound principles have been around for a very long time and it's both a good and a bad thing we can't jump just juicy bits of good, sound, theoretical programming knowledge into the heads of newbie developers as soon as they get going.

I say that's a bad thing since it takes time and effort and a whole lot of mistakes to finally get the good stuff fixed into those developer brains, time we might better employ into building the next thing instead.

And I say it's a good thing since the endless voyage of discovery keeps the appetite up, the enthusiasm up and the flow of warm fuzzies. If you had the wow happen the first time you tried an MVC framework, did you also get the wow going on the first time you spun up a virtual machine using Vagrant? I know I did. And that's very much what I love about this business.

Imagine what your world would be, only for the briefest moment, if PHP stayed with version 5.2. If Zend had the language finished and complete at that point. If your job was only to re-skin yet another WordPress installation because that's all you ever had to do to get an application online. Add in the plugins, re-skin the beast and go through that famous minute install all again for the next one.

Forget clowns and being chased by monsters but still not being able to run away fast enough. This is the very stuff that nightmares are truly made of. Wordpress Over and over again.

Let's not dwell on that particular dystopian vision but move swiftly to brighter imaginings. I'm sure that you have guessed I like to give you a little wander down a dark and fearsome path before dragging you into the warm and sunny glow of the right one. Well, my version of the right one at least.

To do that justice, let me say with thanks and praise that PHP didn't stop at version 5.2, but went on happily to, among many things, a much stronger object model. We know this because some new "Good Stuff" has appeared in the versions that came after. Stuff like namespaces. Stuff like closures.

This then forms the basis for how our explorations into the foundations of PHP-flavoured object oriented programming will continue. This part of the book will explore the concepts and practical implications of the key "juicy" bits of more recent PHP releases in order to extend our arsenal of knowledge, to improve the foundational toolbox that we'll use to fashion awesome codebases. Doing just that will also let us add a little extra polish to the burgeoning shine of our oncoming brilliance.

Before we do all that though, we still need to take a reality check on our understanding of how PHP deals with interfaces. That's coming up in the next chapter.

Come on. Turn the page already.

## More pub time through interfaces.

We have already touched on the concept of interfaces whilst we were discussing abstraction a few chapters back. Within this chapter, we'll bring that idea forward with a more detailed look at both the conceptual interface and the concrete interface as defined through the use of the eponymous keyword.

## An interface is... an interface

Before we get onto the theory of how we should be employing the use of interfaces within our application code, let's just take a brief refresher on how an interface is defined.

```php
<?php
interface InterfaceName
{
    /**
     * Example method definition
     * @var mixed $parameter
     */
    public function methodName($parameter);

    // any other method definitions
}
```

All very straightforward then. Within this very simple interface definition, I've provided for the specification of just a single method, named here as methodName(). All very straightforward indeed.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []); even}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.

Whatever “this, and the other” pertains is up to you as the developer to declare your interfaces. If you need to specify that an object guarantees to accept an array of data and transform it into something else, you might only need a very simple interface declaration as this one:

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

That's a pretty simple guarantee right there, a guarantee that states any object wearing the interface provides the method.

More pub time through interfaces.

> You might be tempted to think that I've forgotten that this isn't a beginner's book but worry no, I'm only including this here to provide a common base from which we can expand our understanding.

Whenever we create an interface in this manner, we are laying down a particular specification that states the methods declared within it will appear in any class that implements the interface. This is frequently referred to as a contract in many places, but I prefer to call it a guarantee. It's a matter of personal preference for me: I feel that the word “guarantee” provides a stronger declaration of intent.

Out there in the real world, contracts rarely make the news unless they've been broken and that's not a connotation that we want to leak into our understanding of interfaces. For our purposes here, we need to consider our interfaces as rock solid, cast iron, impenetrable, unbreakable guarantees. Nevertheless, if the word contract is what you feel more comfortable with, by all means substitute one for the other in the text that follows.

Whenever we code up an object that implements an interface, we are effectively sticking a label, shiny, day-glo orange badge on the object that says “Hey buddy, you don't need to know who or what I am, I'm carrying this guarantee see? You don't need my family history nor my inside leg measurements. You only need this guarantee. With it you can rest assured that I can do this, and the other.
