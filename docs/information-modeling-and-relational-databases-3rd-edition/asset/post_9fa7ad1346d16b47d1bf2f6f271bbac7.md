
![](img/1344db3eba3d550e6edb009556fcd95c_986_0.png)

FIG. 18.17 A data flow diagram for part of the pharmacy subsystem.

The external schemas may now be developed for the various categories of user. It is through the interaction of users with the external interface that the original functions specified in the requirements analysis phase are ultimately executed. Hence, it is important to design the external interface in a way that naturally reflects these functions.

Fundamentally, all that happens when users interact with an information system is that elementary facts are added, deleted, retrieved, or derived. In principle, we could specify the process perspective in terms of these two update and two query operations. But this is too fine a level of granularity for humans to work with efficiently.

We need a way of grouping these elementary operations into larger units. It is often natural to think of operations being performed on significant objects, such as patients and stock items. The major object types abstracted from an ORM schema (see previous section) correspond closely to these object types, and hence provide a good basis for defining operations. The more important classes or entity types in UML class diagrams or ER diagrams provide another good choice for this.

A generic set of external update operations may now be generated with three varieties: add object, delete object, and modify object. Some generic query operations may be generated (e.g., list all facts about an object), but specific queries require an appropriate selection of the relevant fact types (stored or derived).

Users perform such operations through an external interface, typically screen forms or menus. For each screen, we need to consider content (which fact types and operations to include), format (how the screen is displayed), and use (how the operations are invoked by the user). As discussed, default decisions about screen content may be based on operations on the major object types. For example, if Patient is a major object type for the hospital system, a screen is required for it with at least the operations add Patient, modify Patient, delete Patient, show Patient.

Unlike conceptual and logical tables, forms may overlap in their content. This redundancy at the external level conveniently allows users to perform an operation whenever relevant, without having to switch screens. For example, consider the m:n fact type Doctor treated Patient. When working with a Doctor screen, we might query which patients were treated by that doctor. When at a Patient screen, we might query which doctors treated that patient. In the conceptual and logical schemas, facts of this type are stored only once. As long as the external screens have been properly related to the underlying data structures, this overlap is safe. For a discussion on the use of ORM schemas to generate screen forms and transactions, see Campbell and Halpin (1993).

Although there is only one (global) conceptual schema for an application, there may be many external schemas. Different user groups might have different authorization levels that can be specified in access rights tables. This may be done at the conceptual level (e.g., for each fact type, which groups have read, add, delete rights) or at the logical level (e.g., for each table or column, which groups have read, insert, delete, update rights).

Regarding access to options on screen forms, it is generally best to display to users only those options that they are authorized to select. As usual, access rights to screen options may be soft coded as data in tables rather than hard coded in procedures. This avoids having to recompile the forms when access rights are changed, and simplifies reuse of common code. As part of the overall security, passwords are required, and users are given the power to change their passwords.

Apart from access rights, users might also differ in their ability level. Designing application screens to optimize the way various users can perform their tasks is an important aspect of human-computer interface (HCI) design.

Many kinds of interfaces can be used. For example, dialog with the user may use natural language, short questions, command lines, menus, forms, tables, diagrams, images, or sound. Input devices include keyboard, mouse, joystick, pen, and microphone.

In general, the user interface should be easy to learn and easy to use. To achieve this, the interface should be consistent, simple, structured, efficient, and adapted to the user. Let’s examine each of these in turn.

Consistency of interface implies that all the components use the same basic conventions for display format and operations. This promotes positive transfer (learning how to use one screen helps you with the others) and avoids negative transfer. Consistency may be achieved at different levels, such as within the one screen, within the application, among applications from the same company, and with external standards. For example, many Windows applications are being developed nowadays in conformity with Microsoft’s user interface guidelines.

Simplicity of interface implies it is intuitive to use, with minimal effort for users. Each screen should provide the right amount of relevant information (e.g., limit the number of menu options seen at once). Don’t clutter the screen. To allow many operations directly from the one screen, remove all but the main options from the permanent screen display, allowing the user to toggle extra options on as required. For example, use pull-down menus, pop-up windows (e.g., for look-up codes), and status-line help (and pop-up detailed help). To facilitate navigation within and between screens, consider the use of arrow keys for movement, and allow windows and menus to be cascaded or tiled.

Efficiency of interface entails that options may be selected quickly and intuitively. A graphical user interface (GUI) provides a more intuitive means of operation, especially where graphics or sophisticated layouts are involved; here, it is important that “what you see is what you get” (WYSIWYG). However, key-based shortcuts (e.g., hot keys) are sometimes faster and should be provided for the experienced user.

Menu design has a major impact on efficiency. Menus come in various shapes and sizes (full-screen, pull-down, pop-up, ring, button bars, etc.). They provide most, if not all, of the application’s operations. Options on the same menu should be semantically related.

Navigation between menus or screens requires planning (state charts can help here), especially for web-based applications that use hyperlinks to navigate from one place to another. Some navigation patterns are shown in Fig. 18.18. Hyperlink access is typically cyclic.

![](img/1344db3eba3d550e6edb009556fcd95c_988_0.png)

In addition, the following principles should be observed; Order menu options in decreasing frequency of use. Vary color and fonts, but don’t overdo it. For options, use either intuitive icons or terse, clear textual descriptions that are mostly in lowercase. Allow selection of options by mouse clicks or hot keys, and support undo operations.

Adapt the interface to the user as follows. Show only what is relevant to the user. Provide simple procedures for casual users and shortcuts for experienced users. Let users configure the environment to their own taste. Provide levels of context-sensitive help: short messages on status lines, detailed help in pop-up windows. Trap errors as soon as possible and give short and long error messages. Provide online tutorials, user manuals, technical support, and training courses.

If you use some software packages that you find particularly intuitive, have a close look at the interface design and see if you can adapt its good features to your own (as long as you don’t violate any copyright in doing so!). Once you develop your prototype interface, test it on typical users and use their feedback to finesse it.

That’s a quick run through several topics that could easily fill a book on their own. Indeed, whole books are devoted to interface design; many refinements exist for modeling processes, including some very technical approaches that attempt to formally integrate these models with data models. Some interesting work in this regard is referenced in the chapter notes. Various methods and tools are also in common use for associated tasks such as project management (e.g., Gantt charts and PERT charts), testing, performance measures, documentation, and versioning.
