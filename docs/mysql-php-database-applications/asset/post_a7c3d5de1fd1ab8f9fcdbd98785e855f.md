
```php
if ((int)$c['price'] > 0 && $c['price'] != $p->price)
    $child_price = $c['price'];
else
    $child_price = '&nbsp;';
if (!empty($c['description'])
    && $c['description'] != $p->description
)
{
    $child_description = nl2br($c['description']);
}
else
{
    $child_description = '';
}
if (!empty($c['notes']))
{
    $child_description .= " <b
style='color:red'>($c['notes'])</b>";
}
$child_rows[] = table_row(
    anchor_tag(
        $child_url.$c['product_id'], $c['product']
    )
    , $child_price
    , $child_description
);

if (!$child_price_count)
{
    // if no child of this product has its own separate price,
    // print out the product's price now, and set the title of
    // the price column to blank. (this will make that column
    // essentially invisible.)
    if ((int)$p->price > 0)
    {
        print paragraph('<b>Price:</b> ' .$p->price);
    }
    $price_label = '&nbsp;'
}
else
{
    $price_label = '<b>Price</b>'
}
```

```php
if (count($child_rows) > 0)
{
// print out products belonging to this product
array_unshift(
$child_rows
, table_row('<b>Product</b>')
, $price_label
, '<b>Details</b>'
)
);
print paragraph(
table(array('rows'=>$child_rows, 'border'=>0)))
);
}
}
```

## Summary

You might have found this chapter to be quite a handful. In addition to adding code for file uploads, we have used a completely different method for the organization of the code.

The object-oriented approach used in this chapter might not be your cup of tea. And if it's not, you're in good company. Many people who work with PHP feel that object-oriented programming makes little sense in a Web-development environment. But it has its advantages. And the object model in the new version of PHP is greatly enhanced over that of previous versions, too.

As you can see in this application, once the classes are created you don't need to do much to get great functionality within your scripts. Further, in Chapter 14, you can see how we take the code created here and build on it.

## Chapter 13

### Problem-Tracking System

### IN THIS CHAPTER

- Designing a problem-tracking system
- Protecting yourself from redundant data
- Using the `IntegratedTemplate` class from the PEAR class libraries
- Creating a site that has both public and private portions

GOT PROBLEMS? Don't worry, we've all got problems. Relationships falter, bosses make capricious demands, and family – oh, we all know about family. Sadly, in the crazy lives that we all live, PHP and MySQL can do nothing to make your girl/boyfriend love you more or make your dealings with your parents or in-laws any easier. But no scripting language or relational database is better equipped in these areas.

But if you're working for a company that sells or otherwise dispenses goods, it is a virtual guarantee that someone somewhere is going to be unhappy with what he or she has received. When that person complains, you are going to want to have a place in which to record the problems and the steps required for resolution.

The problem-tracking application in this chapter can be used for that purpose. What we have here is fairly generic, and depending on the goods involved with your business, it is likely that you are going to want some fields that apply to your specific products. Anyhow, this application should get you moving in the right direction.

### Determining the Scope and Goals of the Application

This problem-tracking system should have aspects that are publicly available and others that only someone with the proper authorization can view. It makes sense to have a form that users can access over the Web in order to report their problems. Alternatively, someone on the support staff should be able to report problems – for example, while taking a phone call from a dissatisfied customer.

Once the problem is entered, it should be tracked by the staff. Each action taken in the attempt to solve the problem should be noted. And the tracking should have

a public and a private realm – actions that you want the user to see must be differentiated from those that you do not want the user to see.

Those with problems should be able to keep track of them in two ways. They should be emailed whenever a publicly viewable update is made to their case, and a Web page detailing their problem should be available.

### What do you need?

The first thing you need is a form into which people can enter their complaints. What we present in Figure 13-1 is fairly generic; remember that for your own applications you will probably want to add information regarding specific products.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_487_0.png)

Figure 13-1: Problem entry form

Once a problem is entered, there must be a place for the staff to work on the complaint. It should include all the information about the user, the history of the complaint, and a place to enter new information. This problem–update form would look something like the one in Figure 13-2.

The support–staff members need a home, a place where they can log in and see both unassigned tasks and those that are assigned to them and are still open. The staff page would look something like the one in Figure 13-3.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_488_0.png)

Figure 13-2: Problem update form

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_488_1.png)

Figure 13-3: Staff page

If you want to see if any of your users are hypochondriacs, you can use the user-history page shown in Figure 13-4, which lists all problems associated with a user.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_489_0.png)

Figure 13-4: User history page

### What do you need to prevent?

In setting up this part of the application, you're concerned with gathering information efficiently and in a way that's pleasant for the user. Therefore, your worries are more of an interface-design nature, and thus more in the realm of Web design than application development.

Developers, though, are concerned with making sure that the data collected is valid, and complies with database limitations. You might want to endow your forms with some client-side scripting that checks values for obvious problems before sending them in.

### Designing the Database

As you can see from Figure 13-5, the problems table is at the center of the schema.

| Table | Columns |
|-------|---------|
| admin | username, password |
| sources | source_id, source |
| problems | problem_id, customer_id, status_id, summary, problem, entered_by, source_id, entry_dt, modify_dt, last_public_entry, last_entry_id |
| status | status_id |
| history | entry_id, problem_id, entry_type_id, entered_by, source_id, entry_dt, notes |
| customers | customer_id, customer_code, firstname, lastname, address, address2, city, state, zip, zip4, email, day_area, day_prefix, day_suffix, day_ext, day_start, day_end, eve_area, eve_prefix, eve_suffix, eve_ext, eve_start, eve_end |
| staff | staff_id, username, password, staff_name, active |
| entry types | entry_type_id, entry_type |

Here are some design considerations we had to keep in mind as we designed our database:

- Each customer can have one or many problems. The history table records the steps taken to remedy the problem or problems.
- The status table is a lookup table, containing the possible states of a problem, notably open, closed, in processing, and so on.
- The sources table is another lookup table, which records where the problem was originally recorded. If a user enters a complaint over the Web, the sources table will record that; complaints received by the support staff might originate from a phone call, email, or flaming arrow.
- The entry_types table notes whether a specific item in the history table should be public or private. If it is private, it will not be available on the Web page when the user comes to view the progress of the problem, and an email will not be sent to the user when an update takes place. The public updates will be viewable and the user will receive email notification.

Now for a couple of notes on this schema and the create statements that follow. Depending on how you plan on running your site, you may wish to add a table or change a column definition or two.

Notice that we have a problem_code column in the problems table. However, if you will be emailing users regarding the status of problems, you may want something a little less transparent than the following: http://yoursite.com/tracking/problems.php?problem_id=7.

In Chapter 9 we take some precautions when we run into a similar situation. We didn't want people to gain access to restricted parts of our data simply by guessing at variable names in the URL. Here we adopt the same technique we used there in the survey application, creating a random 8-character alphanumeric string from the md5() and uniqid() functions. It's true that we run a risk of the same random number coming up twice, and in fact this approach might not be right for a very large application. But it works here.

Listing 13-1 shows the create statements for the tables we used in this application. In addition to the create statements, this listing includes some of the default data you will need to start the application. Note that if you install this application from the CD-ROM you will have a full set of dummy data you can play with.

### Listing 13-1: create Statements Used in the Problem-Tracking System

```
drop table if exists status;
create table status
(
    status_id   tinyint not null auto_increment
  , status      varchar(20) not null
  , primary key (status_id)
```
