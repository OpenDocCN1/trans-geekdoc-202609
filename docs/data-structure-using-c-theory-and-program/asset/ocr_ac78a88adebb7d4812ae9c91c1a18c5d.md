```
void main()
{
    char ch='y';
    r=NULL;
    while (ch=='y')
    {
        printf("\n 1.Create tree");
        printf("\n 2.Traverse In-Order");
        printf("\n 3.Traverse Pre-Order");
        printf("\n 4.Traverse Post-Order");
        printf("\n 5.Exit");
        printf("\n Enter choioce");
        scanf("%d",&ch1);
        switch (ch1)
        {
            case 1:
                if (insert(&r)==0)
                    break;
            case 2:
                printf("\n\n Left,Root,Right");
                inorder(r);
                break;
            case 3:
                printf("\n\n Root,Left,Right");
                preorder(r);
                break;
            case 4:
                printf("\n\n Left,Right,Root");
                postorder(r);
                break;
            case 5:
                exit(0);
            default:
                printf(" Wrong Choice ");
        }
    } // switch close
} // while close
```