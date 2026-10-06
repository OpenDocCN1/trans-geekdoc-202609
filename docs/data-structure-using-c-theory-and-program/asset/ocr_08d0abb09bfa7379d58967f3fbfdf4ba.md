```
struct dll *next;
};
void create (struct dllnode);
void insert(struct dllnode);
void display(struct dllnode *);
void main()
{
  struct dllnode *node;
  char ch='1';
  node=(struct dllnode *)malloc(sizeof(struct dllnode));
  if(node==NULL)
{
    printf("\n out of memory\");
    exit(0);
  }
  create(node);
  while(ch!='3')
{
    printf("\n 1. Insert at End\");
    printf("\n 2. Display\");
    printf("\n 3. Exit\");
    printf("\n Enter your choice:\\");
    ch=getchar();
    switch(ch)
    {
      case '1':
        insert(node);
        break;
      case '2':
        display(node);
        break;
      case '3':
        break;
      default:
        printf("Wrong Choice\");
    }
  }
```