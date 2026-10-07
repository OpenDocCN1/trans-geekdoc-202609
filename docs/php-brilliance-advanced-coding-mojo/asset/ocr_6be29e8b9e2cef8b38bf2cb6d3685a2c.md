Inheriting vast wealth is not always good.

If all of the child classes conform to and are compatible with the interface that the abstract parent defines, we will never have an issue arising from unexpected variable types being passed to or returned from a method call. The instances of our child classes will all display the attributes and characteristics of the data type that the parent defines.

This all boils down to something that is known as Substitutability and thus forms the central premise of the Liskov Substitution Principle, which I have alluded to before and will cover in much greater depth later in this book. In brief though, substitutability asks us to consider whether our application will execute without a hiccup or a glitch we were to randomly and aribtr switch one child instance with any other child instance from the same inheritance family. If we can switch and swap at will without failure, the indications are strong that we have achieved substitutability. If however, we encounter problems because one instance doesn't quite behave exactly as expected, we have a clear cut case of failing to meet this very desirable goal.

If you'll recall those three rules that I set down earlier on in this chapter? Adhering to those as closely as possible will reduce the potential for type safety related bugs appearing in your application quite significantly.

The knock-on effect of this? Your reputation for having almost supernatural powers of foresight grows just that little bit more.