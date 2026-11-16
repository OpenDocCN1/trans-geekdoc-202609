However, we can make Leak objects always referenced by introducing the following changes into the program:

```
using System;

namespace CLRHeapLeak
{
    class Leak
    {
        private byte[] m_data;
        private Leak m_prevLeak;

        public Leak()
        {
            m_data = new byte[1024];
        }

        public Leak(Leak prevLeak)
        {
            m_prevLeak = prevLeak;
            m_data = new byte[1024];
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Leak leak = new Leak();

            while (true)
            {
                leak = new Leak(leak);
                System.Threading.Thread.Sleep(100);
            }
        }
    }
}
```

Then, if we run the program, we would see in Task Manager that it grows over time. Taking consecutive memory dumps after the start, 10 and 16 minutes, shows that Win32 heap segments have always the same size:

```
0:000> !heap 0 0
Index   Address Name      Debugging options enabled
1: 00530000
    Segment at 00530000 to 00630000 (00003000 bytes committed)
2: 00010000
    Segment at 00010000 to 00020000 (00003000 bytes committed)
3: 00520000
    Segment at 00520000 to 00530000 (00003000 bytes committed)
4: 00b10000
    Segment at 00b10000 to 00b50000 (00001000 bytes committed)
5: 001a0000
    Segment at 001a0000 to 001b0000 (00003000 bytes committed)
```