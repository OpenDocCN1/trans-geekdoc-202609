# Chapter 8 Searching and Sorting

```
{
c=i;
  do
{
    root=(c-1)/2;
    if(a[root]<a[c])
    {
      temp=a[root];
      a[root]=a[c];
      a[c]=temp;
    }
    c=root;
  }while(c!=0);
}
printf("Heap array : ");
for(i=0;i<n;i++)
printf(" %d",a[i]);
for(j=n-1;j>=0;j--)
{
temp=a[0];
a[0]=a[j];
a[j]=temp;
root=0;
  do
{
    c=2*root+1;
    if(a[c]<a[c+1] && c<j)
    c++;
    if(a[root]<a[c] && c<j)
    {
      temp=a[root];
      a[root]=a[c];
      a[c]=temp;
    }
    root=c;
  }while(c<j);
```