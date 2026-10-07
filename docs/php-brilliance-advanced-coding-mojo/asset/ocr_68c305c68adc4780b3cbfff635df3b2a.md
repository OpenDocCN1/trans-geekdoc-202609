# Brain Check

Welcome to the very last chapter of Part Three.
This is the part where we test ourselves on the material that we've covered in this part of the book by asking ourselves, “Could I give a lightning talk on each one of these?”
It’s a checklist and a guide for highlighting areas of further reading.

# Poltergeist

The Poltergeist is an anti-pattern used to describe a short-lived object that bears no state of its own and is used to make things happen to other objects or other parts of the system. An object whose sole purpose is to configure another object is a prime example of a poltergeist.

# Facade Pattern

Facades provide a simplified interface to a more complex subsystem. A distinguishing feature that separates facades from poltergeists is that a facade should be provided with access to the components that it is intended to interact with, whereas a poltergeist reaches out and helps itself.

# Favouring interfaces over implementations

A mechanism for achieving loose-coupling by working with the notion of what a collaborator does, rather than with what a collaborator is. In this way, a consumer may be provided with a collaborator that supports a particular interface and therefore a guarantee of what the collaborator is capable of without the consumer ever knowing the actual concrete type of the collaborator. This allows us to switch different implementations in and without breaking the application.

# Favouring composition over inheritance

Another mechanism for achieving loose-coupling by allowing code reuse through encapsulating the reusable code into its own discrete object. Whereas