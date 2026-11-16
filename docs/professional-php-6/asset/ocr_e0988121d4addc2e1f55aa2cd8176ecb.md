# Load Tolerance

During functional testing, your application will be hit by a combined audience probably not much bigger than your development team — probably less than a dozen simultaneously using the system. In practice, of course, your audience will certainly be much bigger than this, with a requirement for 100, 1,000, maybe even 10,000 simultaneous users to be supported.

You will know the actual figure or estimate from your technical specification, and will have drafted an architecture to suit. What may have worked on paper will not necessary translate to the real world, however. It is vital, of course, that it does.

If the application’s response under heavy load is an unacceptable response time or, worse still, outright failure, then clearly the client will not accept the product as satisfactory.

# Usability

The latest buzzword in interface architecture these days is that of usability. Championed by leading experts such as Jakob Nielsen (see his excellent Web site at www.useit.com), it refers to the inherent intuitiveness and logic of a user interface. It can apply to not only the Web, but also traditional client-side software applications, and even the control panel of a washing machine.

It is typically measured by the ease and speed with which a user new to the application can perform certain tasks. These tasks are expressed as objectives, and no specific instructions on their completion are issued. For example, users of a Web mail application might be asked to compose a new message to foo@example.com. However, they would not be guided to click the Compose button in the top-left corner of the screen, or enter foo@example.com in the recipient box, and so forth.

Observing the user’s effectiveness in carrying out these tasks is the cornerstone of usability testing, discussed shortly.

# Veneer

Just one step removed from usability is the veneer (or finish) of the product. Remember the earlier analogy involving chrome switches and cup holders in the sedan? The veneer of your application is the direct equivalent, and because it is the first real experience users will have of your application, it provides a telling insight into the underlying quality of the application.

What is meant by veneer? Consider the quick-and-dirty examples throughout this book, outside the realm of the larger Widget World project. Each has been constructed to demonstrate a concept, with no other purpose in mind. As a result, they’ve never looked or felt that great — a bit rough around the edges, perhaps. That’s never really mattered, however, because they have merely been demonstrating a technical concept. A finished product should never adapt this approach, of course.

The chrome switches in the driver’s cabin are the properly rendered Previous and Next buttons on your pagination. The cup holders’ smooth eject mechanism is the manner in which the navigation refreshes updates with each section of your application selected. This is the veneer (or finish) of your application, and, although it is not a showstopper if poorly implemented, it can speak volumes about the overall quality of your application.

Many software architects and engineers are less gifted with designing the aesthetics of a user interface than you might think. As part of your own project-management methodology, it is important to ensure