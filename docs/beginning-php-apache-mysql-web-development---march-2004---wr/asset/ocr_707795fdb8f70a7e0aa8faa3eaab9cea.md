# Chapter 9

+   - lair_id_int (11) NOT NULL default 0: Our foreign key to the char_lair table is also an integer of 11, with a default value of 0.

+   - align enum('good', 'evil') NOT NULL default 'good': the align column can be one of two values: 'good' or 'evil'. Because of this, we use an enum datatype, and default it to 'good'. (Everyone has good in them, right?)

You now have a database. We have tables. If you just had to enter some data into your tables in your database, you'd have an application you could give to your users, where they could store information about their favorite superheroes and villains.

You could enter the data with query statements in PHP, but that probably wouldn't be too efficient, not to mention that your users would have any access to it. You would need some sort of interface for them they can use to create and edit data.

Let's design some Web pages for them.

# Creating the Comic Character Application

It's back to the drawing board. Literally. Get away from your computer. We're going to put together some ideas for a Web application.

First of all, you need a page to display a list of comic book characters along with some information about them. It doesn't need to include every detail about them (such as the location of their secret lair), but it should have enough data so that users can distinguish who is who and read a little bit of information about them.

We will list the following information:

+   - Character name (alias)

+   - Real name

+   - Alignment (good or evil)

+   - Powers

+   - Enemies

We also need a character input form. This will serve two purposes. It will allow us to create a new character, in which case the form will load with blank fields and a create button, or it will allow us to edit an existing character, in which case it will load with the fields filled in, and an update button. We also have a reset button that clears the new form, or restores the edited form fields. A delete button should also be available when editing an existing character.

The fields on our form will be as follows:

+   - Character name (alias)

+   - Real name