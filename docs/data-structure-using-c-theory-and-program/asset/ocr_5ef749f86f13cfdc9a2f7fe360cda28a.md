```
printf("\nChoose to do operation :");
scanf("%%d",&i);
switch(i)
{
    case 1 :
    {
        printf("\nEnter the data to be inserted in node :");
        scanf("%%d",&value);
        insert_data(value);
        display();
        break;
    }
    case 2 :
    {
        display();
        break;
    }
    case 3 :
    {
        reverse_list();
        display();
        break;
    }
    case 4 :
    {
        exit(0);
        break;
    }
}

```

# Output

+   1. Insert node
2. display the list
3. reverse the nodes
4. exit