# # Creating the view_member.php Script

The very last PHP file you need to create is the script to view an individual member's details. Save the following code as view_member.php in your book_club folder:

```
<?php
require_once( "common.inc.php" );
require_once( "config.php" );
require_once( "Member.class.php" );
require_once( "LogEntry.class.php" );

$memberId = isset( $_GET["memberId"] ) ? (int)$_GET["memberId"] : 0;

if ( !$member = Member::getMember( $memberId ) ) {
    displayPageHeader( "Error" );
    echo "<div>Member not found.</div>";
    displayPageFooter();
    exit;
}

$logEntries = LogEntry::getLogEntries( $memberId );
displayPageHeader( "View member: " . $member->getValueEncoded( "firstName" )
. " " . $member->getValueEncoded( "lastName" ) );
?>
<dl style="width: 30em;">
    <dt>Username</dt>
    <dd><?php echo $member->getValueEncoded( "username" ) ?> </dd>
    <dt>First name</dt>
    <dd><?php echo $member->getValueEncoded( "firstName" ) ?> </dd>
    <dt>Last name</dt>
    <dd><?php echo $member->getValueEncoded( "lastName" ) ?> </dd>
    <dt>Joined on</dt>
    <dd><?php echo $member->getValueEncoded( "joinDate" ) ?> </dd>
    <dt>Gender</dt>
    <dd><?php echo $member->getGenderString() ?> </dd>
    <dt>Favorite genre</dt>
    <dd><?php echo $member->getFavoriteGenreString() ?> </dd>
    <dt>Email address</dt>
    <dd><?php echo $member->getValueEncoded( "emailAddress" ) ?> </dd>
    <dt>Other interests</dt>
    <dd><?php echo $member->getValueEncoded( "otherInterests" ) ?> </dd>
</dl>
<h2>Access log</h2>
<table cellspacing="0" style="width: 30em; border: 1px solid #666;">
    <tr>
    <th>Web page</th>
    <th>Number of visits</th>
    <th>Last visit</th>
    </tr>
<?php
```