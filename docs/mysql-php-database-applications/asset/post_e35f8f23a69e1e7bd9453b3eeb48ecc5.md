
}
if ($user_id == 0)
{
    // we couldn't find a record corresponding to the claim_code
    // submitted (if any). print out an error and exit.
    $msg = <<<EOQ
    I'm sorry, that doesn't appear to be a valid claim code.
    The URL may not have registered properly.
    Make sure to copy the complete link into your browser and try again,
    or forward your original prize notification to $admin_email.

    EOQ;
    print paragraph($msg);
    exit;
}

Once it is established that a claim code is valid, we want to do a bit of double-checking and make sure that the person who submitted this claim code knows the email address to which the notification was sent. The application does this by displaying a form asking the user to enter the correct email. That form is sent and processed by the form page. When the form is submitted, the following code will execute:

```
$user_email = (string)array_key_value($_POST,'user_email','');

if (!empty($user_email))
{
    // the user has submitted an email address to claim
    // the prize.
    if ($user_email != $winner_email)
    {
        // the email address submitted by the user doesn't
        // match the one stored for the winning entry.
        // display an error message.
        $notice = <<<EOQ
        I'm sorry, that email address doesn't match our records.
        Please try again, or forward your original prize notification
        to $admin_email.

        EOQ;
    }
}
```

The comparison $user_email != $winner_email will work because the query that ran at the top of the page retrieved the correct winner's email, and we get $user_email from the form submitted by the user. If that comparison fails, an error message prints. If it does not fail, the following code updates the winners database, recording the time the prize was claimed, and sends an email to the winner letting him or her know that the claim was successful:

```
else
{
// everything matches. we can update the database
// to record a valid claim.
$claimquery = "update winners set claim_dt = now()
where user_id = $user_id
and claim_code = '$claim_code'
and weekday = '$weekdate'
";
my_query($claimquery);
if (mysql_affected_rows() > 0)
{
// send a notification to the administrator that
// the prize has been claimed.
$confirm_url = regular_url('admin/winners.php');
$msgtext = <<<EOQ
The prize for $weekdate has been claimed by $user_email.

Confirm the prize at

$confirm_url
EOQ;
```

```
$subject = 'Prize Claim';
$result = mail($admin_email,$subject,$msgtext);

if ($result)
{
// we don't need to re-display the form now.
// print out congratulations and bail.
$msg = <<<EOQ
Thanks! Your claim has been accepted.
Your prize should be on its way soon!

EOQ;
print paragraph($msg);
exit;
}
```

```
else
{
    $private_error = <<<EOO
could not send claim notification:
admin_email=($admin_email)
subject=($subject)
msgtext=($msgtext)
EOO;
    user_error('Warning: Could not notify administrator
of your claim.', E_USER_WARNING);
}
```

```
else
{
    // just in case the database is broken or
    // some other horror has occurred...
    $msgtext = <<<EOO
The prize for $weekdate has been claimed by $user_email, but the
database
update did not work.
EOO;
    $subject = 'Prize Claim';
    $result = mail($admin_email,$subject,$msgtext);
    if (!$result)
    {
        $private_error = <<<EOO
could not send claim problem notification:
admin_email=($admin_email)
subject=($subject)
msgtext=($msgtext)
EOO;
        user_error('Warning: Could not notify administrator
of your claim.', E_USER_WARNING);
    }
```

```
// let the user know that something broke
// and re-display the form by continuing
// with the script.
$notice = <<<EOO
Your claim is valid, but we were unable to record that fact.
Please try again later, or forward your initial prize notification
to $admin_email and let them know there was a problem.
EOQ;
```

```
)
)
)
```

The final portion of this page simply prints the form in which the user will enter his or her email. There's really no need to show that here.

## Summary

The survey application involves quite a bit of code, but it isn't anything that you shouldn't be able to figure out with some close scrutiny of the files and the comments. Take a look at the complex_results.php page and its includes (age_results.php, state_results.php, and country_results.php) for a look at how MySQL aggregate functions can come in handy.

This application contains much more complexity than the guestbook. In it is a real database schema complete with related tables. In the course of the application we need to make use of queries that contain MySQL functions. (See Appendix J for more information on MySQL functions.)

Another notable item seen in this chapter is the function set we've created for creating common HTML elements. Whether you want to make use of such functions or not is up to you. You may prefer typing out individual form elements, tables, and the like. But you will be seeing these functions used in the remainder of this book.

## Part IV
### Not So Simple Applications

- CHAPTER 10 Threaded Discussion
- CHAPTER 11 Content-Management System
- CHAPTER 12 Catalog
- CHAPTER 13 Problem-Tracking System
- CHAPTER 14 Shopping Cart
- CHAPTER 15 XML Parsing
- CHAPTER 16 SOAP
- CHAPTER 17 Project Management

## Chapter 10
### Threaded Discussion
### IN THIS CHAPTER

- Adding to your Web site features that promote community
- Using an advanced technique to write functions
- Looking at other criteria to use when designing a database
- Setting up error-handling and debugging functions

IF YOU'VE CREATED a Web site or are looking to create one, it's probably safe to assume that you want people to return frequently to your pages. But as everyone in the Web industry knows, loyalty is fleeting, and people are always looking for something better, more engaging, or closer to their interests.

One way to keep the anonymous masses involved with your site is to offer your visitors a way to contribute to its content. If someone has accessed your site, it's likely that he or she has an opinion on the topic you are presenting. And if our conclusions from 30-plus years of observation are correct, people love to share their opinions.

Using the threaded-discussion application in this chapter, you can create an area on your Web site where your users can share their opinions and interact with you and each other.

Once you have this piece of your site up and running, you are well on your way to creating your own Web community. I make special mention of the word community for two reasons.

- First, it is a huge buzzword within the industry. Everyone is looking to create a sense of familiarity and inclusion that tempts users to return.
- Second — and perhaps more importantly — you, the Webmaster, should know what you're getting yourself into. From personal experience, we can tell you that "community" can be a real pain in the butt. On the Web, everyone is pretty much anonymous, and few consequences are associated with antisocial behavior. Thus, in many discussion groups, opinionated windbags have a way of ruining a promising discussion.

Before too long, you will undoubtedly see things that are mean or distasteful, and you must be prepared to deal with it. We're not trying to scare you away from including a discussion list on your site. We're just letting you know that you need to put some effort into administering it. Whether you monitor the list yourself or appoint someone to do it for you, somebody will need to make sure your users behave if you want it to be orderly and functional.

## Determining the Scope and Goals of the Application

The purpose of any discussion board is reasonably simple. Any visitor to the site should be able to post a new topic to the board or reply to any of the existing topics. Furthermore, the board must be flexible enough to deal with any number of replies to an existing topic, or replies to replies, or replies to replies to replies, and so on. Put another way, the board must be able to deal with an indefinite level of depth. The script must be able to react appropriately, whether the discussion goes one level deep, five levels deep, or ten levels deep, which requires some new techniques, both in your data design and in your scripts.

## What do you need?

You need only two files to generate all the views needed for this application. But these two files can have very different looks, depending on the information that is displayed.

The first file displays topics and their replies. The first time users come to the message board they will not know what threads they wish to read. Therefore, a list of topics will be displayed. Figure 10-1 shows the list of top-level topics.

Once a user chooses a topic the page lists all the posts within that topic. As you can see in Figure 10-2, the top of the page shows the text and subject of the post being read. Below that, immediate replies to that post are indicated with a colored border, and the text of the immediate replies is also printed. Figure 10-2 also shows that the application provides a subject, a name, and a link to posts that are more than one level deep in the thread. You can see that it is rather easy to tell who has replied to what.

This same page provides another view. If a user clicks through to a post that does not start a topic, the page shows all threads beneath that post. At the top of the page the script will print the top-level post (or root) and the post immediately prior to the one being viewed (or parent). Figure 10-3 shows an example of this view.
