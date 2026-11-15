```
displayThanks();
} else {
    displayPageHeader( "Sign up for the book club!" );
?>
<p>Thanks for choosing to join our book club.</p>
<p>To register, please fill in your details below and click Send
Details.</p>
<p>Fields marked with an asterisk (*) are required.</p>
<?php
    $renderer = new HTML_QuickForm_Renderer_Tableless();
    $form->accept( $renderer );
    echo $renderer->toHtml();
    displayPageFooter();
}

function addElements( $form ) {
    $form->addElement( "text", "username", "Choose a username" );
    $password1 = $form->addElement( "password", "password1", "Choose a
password" );
    $password1->setValue( "" );
    $password2 = $form->addElement( "password", "password2", "Retype
password" );
    $password2->setValue( "" );
    $form->addElement( "text", "emailAddress", "Email address" );
    $form->addElement( "text", "firstName", "First name" );
    $form->addElement( "text", "lastName", "Last name" );
    $genderOptions = array();
    $genderOptions[] = HTML_QuickForm::createElement( "radio", null,
null, "Male", "m" );
    $genderOptions[] = HTML_QuickForm::createElement( "radio", null,
null, "Female", "f" );
    $form->addGroup( $genderOptions, "gender", "Your gender", "" );
    $member = new Member( array() );
    $form->addElement( "select", "favoriteGenre", "What's your favorite
genre?", $member->getGenres() );
    $form->addElement( "textarea", "otherInterests", "What are your
other interests?", array( "rows" => 4, "cols" => 50 ) );
    $buttons = array();
    $buttons[] = HTML_QuickForm::createElement( "submit", "submitButton",
"Send Details" );
    $buttons[] = HTML_QuickForm::createElement( "reset", "resetButton",
"Reset Form" );
    $form->addGroup( $buttons, null, null, "&nbsp;" );
}

function addRules( $form ) {
    $form->addRule( "username", "Please enter a username", "required" );
    $form->addRule( "username", "The username can contain only letters and
digits", "alphanumeric" );
    $form->addRule( "password1", "Please enter a password", "required" );
    $form->addRule( "password1", "The password can contain only letters and
```