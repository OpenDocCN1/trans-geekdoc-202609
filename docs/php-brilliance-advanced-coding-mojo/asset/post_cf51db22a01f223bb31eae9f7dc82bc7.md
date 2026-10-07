
# Talking points.

We have arrived at the end of Part Two and in doing so, we are reaching the end of the foundational aspects of PHP Brilliance. Before we move on to the fascinating topics of programming principles, paradigms and design patterns, there are still a few things that we need to tie up.

So here we are again at another “Talking points".

## So, which is it? Contract or guarantee?

Way back in the chapter on interfaces, I expressed a preference for the word guarantee. This is despite the fact that the rest of the world calls them contracts. Just to be clear, I’m not about to make a stand on the issue and declare that the rest of the world is wrong. That would be plain silly.

Nevertheless, I think there is some value in exploring these ideas in here and away from the interface chapter itself. As I mentioned previously, it’s largely a matter of preference. The end result should be the same: we are looking for an enforceable agreement.

In normal circumstances, a contract refers to something in which two or more parties come to a mutual agreement. For instance, you enter into a contract of sale whenever you visit a store to exchange cold, hard cash in return for the latest-selling, dancing techno-gadget. Or whenever you pay for another Minecraft content pack download. It’s a contract because each party gives something and receives something back, based on these mutually agreeable terms. You agree to provide money and receive a product. The store agrees to provide a product and receive money.

That being, the concept of the contract in this case stems from the Design By Contract approach laid down by Bertrand Meyer in 1986, and is subsequently thoroughly documented in his book Object Oriented Software Construction.

> ¹https://archive.eiffel.com/doc/manuals/technology/contract/

Talking points.

200

> Design By Contract (DbC) is an idea worth reading up on, even though it's geared towards creating software in Eiffel. However, following DbC to the letter leads to violations of the Liskov Substitution Principles (coming up in Part Four) and therefore leads to application code that is not type safe. Just so that you know.

In contrast to, this guarantee is typically a one-sided affair, a unilaterally made promise to honour the guarantee itself. When the terms of the guarantee are written out, it's quite often so without knowing who the interested parties are going to be.

At the end of the day, the question of whether it should be considered a contract or a guarantee is rather a moot point. The contract term applies perfectly when you consider the two parties involved in a logical process, the object and the client code that is collaborating with it.

The proposal of the term guarantee, being a much more unilaterally made arrangement, is offered with regard to the intended audience, the readers of our code.

When a white goods manufacturer ships a brand new refrigerator, they will include a written guarantee (warranty) with it. A guarantee is, in theory, as a unilaterally made agreement to fix or replace the appliance in the event of a failure. If the appliance works perfectly during the guarantee period, then guarantee is unlikely to be taken up.

In other words, whoever purchases that refrigerator has the option to read the terms and conditions set out in that guarantee and in doing so will hopefully understand how a contract of service may be entered into with the manufacturer should the ever arise. The manufacturer has no idea who will end reading this document, nor indeed whether they are able to decipher the jargon and legalese that peppers the small print.

In essence, this is the idea that I'm putting forward. In the process of mentoring colleagues, I want to suggest that these interfaces are to lay down the terms and conditions of engagement. To be read and understood prior to writing the code that will utilize these things, which is the point where the contract analogy becomes more appropriate. Contracts for code, guarantees for coders.

At the end of the day, it doesn't amount to a hill of beans, as long as the underlying concept is understood within our respective teams.

## Duck typing

I made a brief reference to the concept of duck typing in the previous chapter so I think it's appropriate to bring it in here for a little look-see, especially given that we've literally just gone through that guarantee/contract malarkey. As you might have gathered already, I'm much more in favour of the guarantee style approach since we're less likely to run into problems further down the line that way.

Regardless, duck typing is the act of checking for what an object can do in order to see if it can do what you want it to.

What does that even mean?

Rather than testing for the presence of a guarantee either through type hinting or testing against the instanceof keyword, duck typing relies on a check to see if a method or property exists prior to invoking that method or reading that property.

The notion is based on a quotation by the nineteenth century poet, James Whitcomb Riley, who once said:

> When I see a bird that walks like a duck, swims like a duck and quacks like a duck, I call that bird a duck

What this leaves us with the idea that we are simply checking for the existence of a method, a characteristic, to determine whether that object is useful to us.

To transpose Mr Riley's quotation into code, it is effectively the same as saying that if an object provides a quack() method, then the object can be treated as if it's an instance of a Duck regardless of whether it is or not.

In code, this might look like:

```php
public function doStuff($param)
{
    if (is_callable(array($param, 'quack'))) {
        return call_user_func(array($param, 'quack'));
    }
}
```

Talking points.

203

This isn't the approach we're going to take though. It isn't the way to achieve PHP Brilliance. There's a little too much reliance on the right thing coming in as a parameter, and you've already had to suffer squawking about exceptions in constructors and likening the process to sticking your head in the waste disposal.

> I promise, we'll be discussing Instantiaphobia, which includes this whole constructor business, in very short order - coming up in Part Three no less.
