```
default:
    // Illegal action
    crack_attempt();
}
}
main($action);
?>
```

As expected, viewing `privilege.php` brings us to the selection screen. Since there are no privileges in the system, yet, we can only add a new one:

![](bbox=[0.18, 0.29, 0.83, 0.53])

If we enter our first privilege in the text element and click "Save", we are brought back to the selection screen. Our new privilege "Stay out late" appears in the `<select>` element:

![](bbox=[0.18, 0.6, 0.83, 0.81])

Next we could test the ability to edit privileges by clicking "Change Privilege" and changing the description to "Edit user profiles". Once all of the functionality has been tested (delete, cancel, and so on) we are ready to work on `userprivilege.php`.