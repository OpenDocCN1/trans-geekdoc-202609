And favour Composition too.

just need to make sure it gets the appropriate state instance. This is a huge plus
 a busy application.

At the time of writing we're on the verge of an exciting time with several projects attempting to crack the stateful PHP application next. Instead of the boot->shutdown lifecycle of a regular PHP script, great strides are being made in producing PHP application servers that are able to maintain context and state multiple requests. We need to keep our eyes on the likes of Appserver.io* and ReactPHP* as these could very well negate the need for caching as we know today.

> http://appserver.io
http://reactphp.org/

# The Strategy Pattern

Closely related to the State Pattern is this one, the Strategy Pattern. In some cases, they're so closely related that it's difficult to tell them apart. Imagine for a moment Lizzie has an identical twin, Lottie. They look exactly alike. The dress exactly alike. The only way to tell them apart is when they're eating ice-cream since Lizzie will be the one fiercely guarding the we of pistachio, chocolate and mint. Lottie on the other hand is rather partial to Ben & Jerry's "Pphish Food".n

Ouch. Sorry.

Fortunately, the State and Strategy patterns aren't quite as to tell apart at that. Again, we're going to be injecting some encapsulated behaviour by this time, that behaviour will represent a custom algorithm that will operate on things, usually data, external to itself.

This is a key part of the distinction between the State and the Strategy patterns. Whereas the State pattern provides for interchangeable behaviour based on some notion of the internal state of the implementer, the Strategy patterns provides for interchangeable behaviour based on some notion of how we want things to be processed by those behaviours.

*