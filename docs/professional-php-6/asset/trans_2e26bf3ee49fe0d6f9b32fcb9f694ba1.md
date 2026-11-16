

```
$message .= "\r\n";
return ($message);
}
function generateContactEmail(&$user, &$contact,
$contactVisits, $flagBase64=true) {
    global $GLOBALS;
    require_once ($GLOBALS["smarty-path"].'Smarty.class.php');
    $smarty = new Smarty;
    $smarty->assign_by_ref ("user", $user);
    $smarty->assign_by_ref ("contact", $contact);
    $smarty->assign_by_ref ("contactVisits", $contactVisits);
    $smarty->assign('start_weeks', getStartWeeks());
    $smarty->assign('current_start_week', $contact->week_start);
    $smarty->assign("max_weekly_contacts", $GLOBALS["max-weekly-contacts"]);
    $email_body = @$smarty->fetch('customer-contacts.tpl');
    $headers = "";
    $headers .= "From: ".$GLOBALS["email-from"]."\n";
    $headers .= "To: ".$user->email."\n";
    if (strlen ($GLOBALS["email-contact-cc"]) > 0)
    $headers .= "Cc: ";
    $headers .= $GLOBALS["email-contact-cc"];
    $headers .= "\n";
    if (strlen ($GLOBALS["email-contact-bcc"]) > 0)
    $headers .= "Bcc: ".$GLOBALS["email-contact-bcc"]."\n";
    $mime_boundary = "<<<===".md5(time())."";
    $headers .= "MIME-Version: 1.0\r\n";
    $headers .= "Content-Type: multipart/mixed;\r\n";
    $headers .= " boundary=\"".$mime_boundary."\"";
    $message = "";
    $message .= "This is a multi-part message in MIME format.\r\n";
    $message .= "\r\n";
    $message .= "--".$mime_boundary."\n";
    $message .= "Content-Type: text/plain; charset=\"iso-8859-1\"\r\n";
    $message .= "Content-Transfer-Encoding: 7bit\r\n";
    $message .= "\n";
    $message .= $GLOBALS["email-contact-message"]."\n";
    $nextEnding = "\r\n";
    $message.=mimeifyContent($email_body,$mime_boundary,
        "customer-contact", $flagBase64);
    $message.="--".$mime_boundary."".$nextEnding;
    $subject = $user->emp_id. " ".$user->last_name. " : ".$user->email_subject;
    return array ($user->email, $subject, $message, $headers);
}
```

Note two things here. One, you’re calling $smarty->fetch() instead of $smarty->display(). The fetch function places the HTML output into a variable, rather than to the screen, as does the display function.

Two, for technical reasons, it’s safer to base64-encode HTML output if there is any chance of it using non-7-bit ASCII (e.g., if you’re using Unicode or non-English characters). However, base64-encoding the HTML in the e-mail makes it practically untestable, which is why the $flagBase64 argument exists.

If this function contained the function to physically mail the e-mail instead of simply creating the content, then you would most certainly create and utilize a mock object that simulated the e-mailing API and didn’t base64-encode the content.

## Summary

With this chapter, the Widget World software development effort is concluding. You would be correct in pointing out that not all the stories and features have been completed, but we have no desire to be historical revisionists of this real-world example or to force you through another 100 redundant pages of the same procedure. By now, you have the tools and know-how to complete it yourself.

Testing is one aspect of software development that has historically been considered little more than “busywork,” but you’ve experienced how test-driven development can help you not only develop your code, but also find bugs and continue to test even when you’re working on distant parts of the system.

Refactoring is not just a technical term for “code cleanup.” Ideally, it shouldn’t even be considered a distinct task from software development. Refactoring is simply a coding priority, much in the same way that developing system objects is a coding priority too. Plus, you’ve seen how constant refactoring can help to develop a complex framework without the need for excessive analysis and unused features.

These are just a few of the principles of extreme programming (XP), which is designed to reduce complexity in order to sustain development by keeping your code base nimble and flexible. Although not every project is a candidate for the complete methodology of XP, that does not mean that your methodology, whether it’s spiral, waterfall, or RUP, cannot benefit from some of the practices such as testing and constant refactoring. Additionally, because of a lack of peer programmers (for you, the reader), as well as space and focus on code, many aspects of XP haven’t formally been examined, such as planning for a release and measuring the project metrics. XP is quite a disciplined approach, and you should learn more about it, because its strengths and rewards are solidly concerned with the subtleties of software development as a team.

Of course, no matter how methodical and diligent your approach during the build process, you can’t skip the most important part of any project — quality assurance. That’s something you’ll meet in Chapter 20, as you discover what steps you can take post-build to ensure that your project features the quality levels your clients have a right to expect.

## Quality Assurance and Testing

The Widget World sales force automation toolkit site is looking pretty good. You’re on schedule and on budget, and the client is, thus far, happy with the beta version running on your development environment and staging server. Furthermore, by employing rigorous unit testing throughout the build process in Chapter 19, you can be sure that the individual components that comprise the application all function more or less correctly independently; hence, there shouldn’t be any deep-rooted problems in the code itself.

At this point, you might well be tempted to let your guard down. In fact, you have now reached one of the most critical stages in the entire project. The application is more or less complete, and the client is urging you to let them use it. You must resist, however.

Quality assurance (QA) is a term you might be familiar with. Indeed, it is borrowed from traditional manufacturing and engineering processes, and is the kind of procedure you expect to be carried out on your new DVD player or luxury family sedan. Why would you not, therefore, want to apply it to something as complex and crucial as your application?

This chapter introduces you to the QA process in large-scale PHP projects. You’ll learn why quality assurance is of great importance, and what it means in terms of your expectations and those of your client. You’ll also learn about the kinds of testing you must do in order to be able to confidently give your application a seal of approval, and how to get your team on board to help you when things go wrong.

## Introduction to QA

Somewhat understandably, expectations regarding the reliability of the Web and the Internet at large are still pretty low among its everyday users. Chances are good that you’ve had a client or two call you recently to say that their e-mail was down, and so they might not have received anything you’ve sent. Maybe you’ve tried to order something online recently, only to be kicked off while your credit card was being processed. Or maybe your friend’s ISP has been down for a couple of days, and no one in tech support seems to be able to tell him when he’ll be back online again.

## Part III: A Real-World Case Study

Scenarios like this are all too common. What is truly shocking is that the parties involved typically shrug their shoulders and accept it. Your clients didn’t sound surprised when they told you that e-mail was down. You probably didn’t even curse under your breath when your online order went wrong. And your friend likely shrugged his shoulders and got out his 3G data card.

This is a phenomenon still more or less unique to the Internet. If you bought a new car and it stalled on the highway just weeks later, you’d be pretty mad at your dealer. If you ordered a mocha latte before work and your barista gave you a cappuccino， you’d be mad and insist on a new cup. And if your DVD player died soon after purchase, you’d take it back.

There are two reasons why people don’t get upset when the Internet doesn’t work right. First, most people reason that there’s something innately complicated about the Internet, and that it must go wrong as a result. This is a non sequitur, of course. Yes, the Internet is complicated, but so is your DVD player. In practice, too, the underlying infrastructure (that is, the servers, routers, and so forth) of the Internet is pretty much rock solid. It’s bad programmers who cause things to break with the bad code they write, and the poor decisions they make when developing.

The second and more crucial reason applies to those who have had previous experience with Internet application developers. Frequently, their past experiences with these agencies and individuals have been such that their expectations with present vendors have hit rock bottom. In fact, and unfortunately, there are few other industries in which such an explosion of dangerously under-skilled labor has occurred in the past few years. This has manifested itself in both appalling freelance Web “professionals” (who can barely produce valid XHTML, let alone high-quality back-end code), and some truly awful digital agencies (that revel in producing self-indulgent “award-winning” creative work without so much as a nod to how well it works under the hood). Excellence is the exception rather than the rule. In effect, there are literally thousands of vendors who talk the talk, but don’t walk the walk.

The more cynical inference from this observation is that because your client’s expectations will be low, you should aim low, too, because they’re not likely to get mad at you if things go wrong. This approach, however, is not only cynical, it is also not commercially sensible.

## Why You Should Aim High

Aiming to have a high-quality product before handing over to the client is not just about keeping the client happy. It’s about maintaining your own sanity, too.

It is inevitable that your assembled system will (initially, at least) be functionally defective in some way. This does not necessarily mean that it will malfunction in the traditional sense. It could be slow when real-world data is applied, or have some unforeseen business logic error. A systematic approach to QA prior to handover ensures the following:

- Developer time, and hence cost spent on resolving defects, is minimized through a thorough, structured approach.
- The team’s timely transition onto other projects can be closely adhered to.
- Problems encountered during deployment can be isolated as being unrelated to the application itself.

