contains a stub function whose name and arguments match the name and arguments of one of the DLL’s functions. The stub function calls its corresponding function in the DLL. During the compile process, the linker incorporates the code in the library file into the application’s executable file. When the application calls a function in the library file, the function of the same name in the DLL executes.

The DLLs included with Windows are typically stored in the %SystemRoot%\system32 folder. Windows searches this folder when an application calls a DLL function. The library and header files for Windows API functions are included in the Windows DDK.

To include a API function in an application, you need to do the following:

+   1. Add the library files to the project. In Visual Studio, click Project > Properties > Linker > Input. In the Additional Dependencies box enter the names of the .lib files. If needed, you can enter a path for the library files in the Linker > General window under Additional Library Directories.
+   2. Include the header files in one of the application’s files. Here is an example:

```
extern "C" {
#include "hidsdi.h"
#include <setupapi.h>
}
```

The #include directive causes the contents of the named file to be included in the file, the same as if they were copied and pasted into the file. The extern "C" modifier enables a C++ module to include header files that use C naming conventions. The difference is that C++ uses name decoration, also called name mangling, on external symbols.

To add a path to an include directory, in Visual Studio, click Project > Properties > Resources > General. In the Additional Include Directories box enter the path(s) to your .h files. (On a command line, these paths are in the compiler’s /I option.)

The punctuation around the file name determines where the compiler will search for the file, and in what order. This is relevant if you have different versions of a file in multiple locations! Enclosing the file name in brackets