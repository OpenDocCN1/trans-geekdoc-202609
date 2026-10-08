```
Bacon <input type="checkbox" name="cb_bacon" value="Y" />
Sausages <input type="checkbox" name="cb_saue" value="Y" />
Beans <input type="checkbox" name="cb_beans" value="Y" />
```

Checkboxes work in a different way to a textbox. For each tag, I've specified a name and a value. If the visitor ticks the box, the specified variable name will be set to the specified value. If the visitor leaves the box unticked, the specified variable will be blank. So, for example, if the visitor ticks the "Bacon" box, $cb_bacon$ will be equal to "Y". If he leaves it unticked, $cb_bacon$ will be blank.

Finally we need to name the radio buttons. Again, these work in yet another slightly different way.

The code for the radio buttons is currently:

```
Fried <input type="radio" name="radio" />
Poached <input type="radio" name="radio" />
Scrambled <input type="radio" name="radio" />
```

Amaya has given the radio buttons a name, but we're going to change it. Change the HTML tags to:

```
Fried <input checked type="radio" name="rb_eggs" value="F" />
Poached <input type="radio" name="rb_eggs" value="P" />
Scrambled <input type="radio" name="rb_eggs" value="S" />
```

A couple of important things to note about these radio buttons. See how the first radio button (fried) includes the word "checked". This means that, when the form is displayed, this is the option that will be selected by default. You don't have to check any radio button like this but, if you do, make sure you only check one of them.

Next, see how each radio button has the same name ($rb_eggs$) but a different value (F, P or S). If the visitor clicks the "Fried" button, $rb_eggs$ will be set to "F". If he chooses "Poached", $rb_eggs$ will be "P" and so on. Each "set" of radio buttons on a form, ie each collection from which the visitor can make one choice, needs to have its own name that is shared among all the buttons in the set but which is not used anywhere else on the form.

As to why I've used values of F, P and S rather than "Fried", "Poached" or "Scrambled", this is mostly personal preference. And because it saves me having to remember whether the value of a radio button is Fried or FRIED or fried when I come to check it in the PHP program.