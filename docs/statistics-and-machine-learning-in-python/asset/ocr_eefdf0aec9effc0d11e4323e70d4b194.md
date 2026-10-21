# PYTHON LANGUAGE

Source Kevin Markham https://github.com/justmarkham/python-reference

# 3.1 Import libraries

```
# 'generic import' of math module
import math
math.sqrt(25)

# import a function
from math import sqrt
sqrt(25)    # no longer have to reference the module

# import multiple functions at once
from math import cos, floor

# import all functions in a module (generally discouraged)
# from os import *

# define an alias
import numpy as np

# show all functions in math module
content = dir(math)
```

# 3.2 Basic operations

```
# Numbers
10 + 4      # add (returns 14)
10 - 4      # subtract (returns 6)
10 * 4      # multiply (returns 40)
10 ** 4     # exponent (returns 10000)
10 / 4      # divide (returns 2 because both types are 'int')
10 / float(4)  # divide (returns 2.5)
5 % 4       # modulo (returns 1) - also known as the remainder

10 / 4      # true division (returns 2.5)
10 // 4     # floor division (returns 2)
```