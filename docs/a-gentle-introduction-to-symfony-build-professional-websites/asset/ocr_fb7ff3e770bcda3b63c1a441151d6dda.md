decoration process), and the partials are executed when they are called in a template. Does it sound too abstract? Let’s see an example.

Imagine a layout with one zone for the template and two slots: one for the sidebar and the other for the footer. The slot values are defined in the templates. During the decoration process, the layout code wraps the template code, and the slots are filled with the previously defined values, as illustrated in Figure 7-4. The sidebar and the footer can then be contextual to the main action. This is like having a layout with more than one “hole”.

# Figure 7-4 - Layout slots defined in a template

![](bbox=[0.116, 0.221, 0.766, 0.321])

Seeing some code will clarify things further. To include a slot, use the include_slot() helper. The has_slot() helper returns true if the slot has been defined before, providing a fallback mechanism as a bonus. For instance, define a placeholder for a ‘sidebar’ slot in the layout and its default content as shown in Listing 7-14.

# Listing 7-14 - Including a ‘sidebar’ Slot in the Layout

```
```php
<div id="sidebar">
<?php if (has_slot('sidebar')): ?>
    <?php include_slot('sidebar') ?>
<?php else: ?>
    <!-- default sidebar code -->
    <h1>Contextual zone</h1>
    <p>This zone contains links and information
    relative to the main content of the page.</p>
<?php endif; ?>
</div>
```
```

As it’s quite common to display some default content if a slot is not defined, the include_slot helper returns a Boolean indicating if the slot has been defined. Listing 7-15 shows how to take this return value into account to simplify the code.

# Listing 7-15 - Including a ‘sidebar’ Slot in the Layout

```
```php
<div id="sidebar">
<?php if (!include_slot('sidebar')): ?>
    <!-- default sidebar code -->
    <h1>Contextual zone</h1>
    <p>This zone contains links and information
    relative to the main content of the page.</p>
<?php endif; ?>
</div>
```
```

Each template has the ability to define the contents of a slot (actually, even partials can do it). As slots are meant to hold HTML code, symfony offers a convenient way to define them: just write the slot code between a call to the slot() and end_slot() helpers, as in Listing 7-16.

# Listing 7-16 - Overriding the ‘sidebar’ Slot Content in a Template

```
```php
// ...
<?php slot('sidebar') ?>
```
```