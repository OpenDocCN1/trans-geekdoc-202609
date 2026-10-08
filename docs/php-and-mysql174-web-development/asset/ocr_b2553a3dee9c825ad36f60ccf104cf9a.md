You should get output similar to the following:

```
------+------+
| @1 |
+------+
|  3 |
+------+-
```

1 row in set (0.00 sec)

You can check for yourself that the calculation is correct.

# Triggers

Triggers are a type of event-driven stored routine or callback, if you prefer. They are code associated with a particular table that is invoked when a particular action is taken on that table.

The basic form of a trigger is as follows:

```
CREATE TRIGGER trigger_name
{BEFORE | AFTER} {INSERT | UPDATE | DELETE} ON table
[order]
FOR EACH ROW
BEGIN

END
```

The first line names the trigger to be created. The combination of the timing (BEFORE or AFTER) and the event that invokes the trigger (INSERT, UPDATE, or DELETE on the named table) specify the code in the body of the trigger will run.

The optional order clause allows you to run more than one trigger on a particular time/event combination. The format of this clause is

```
{FOLLOWS | PRECEDES} other_trigger
```

The EACH ROW clause means that the trigger is executed for each affected row in the triggering query.

Let's look at a simple example. This code is shown in Listing 13.5.

# Listing 13.5 trigger.sql—Deleting an Order

```
# Trigger example

DELIMITER //

# delete order_items before to avoid referential integrity error
CREATE TRIGGER Delete_Order_Items
BEFORE DELETE ON Orders FOR EACH ROW
```