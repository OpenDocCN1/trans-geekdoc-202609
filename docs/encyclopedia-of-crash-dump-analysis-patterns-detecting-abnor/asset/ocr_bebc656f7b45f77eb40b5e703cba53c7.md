Here's the source code of the modeling application:

```
```c
typedef void (*PFUNC)(void);

typedef struct _MyStruct_tag
{
    int data;
    PFUNC pfunc;
} MYSTRUCT;

void bar(MYSTRUCT *ps)
{
    ps->pfunc();
}

void foo(MYSTRUCT *ps)
{
    bar(ps);
}

int main(int argc, const char * argv[])
{
    MYSTRUCT pstruct = {10, NULL};

    foo(&pstruct);

    return 0;
}
```
```