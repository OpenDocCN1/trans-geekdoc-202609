# Managed Space

We recently encountered **Invalid Handle** pattern in the context of .NET program execution. We decided to model it and wrote a small C# program:

```
namespace SafeHandle
{
    class Program
    {
        static void Main(string[] args)
        {
            SafeFileHandle hFile =
                new SafeFileHandle(new IntPtr(0xDEAD), true);
            Console.WriteLine("About to close");
            Console.ReadKey();
        }
    }
}
```

Of course, when we execute it nothing happens. Invalid handles are ignored by default. However, to change the behavior we enabled “Enable close exception” in gflags.exe:

![](bbox=[0.26, 0.45, 0.74, 0.81])