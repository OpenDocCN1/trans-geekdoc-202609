To do this, the method builds nine 3-character strings from the data in the grid and compares each one to the strings "XXX" or "000", until a match is found or none exists. If a match is found, the corresponding letter is returned; otherwise, the empty string is returned. Here is the code for this method:

```
def _hasWinner(self):
    """Returns the letter of the winner or the empty string
    if there is no winner."""
    row0 = self._getString(0, 1, 2)
    row1 = self._getString(3, 4, 5)
    row2 = self._getString(6, 7, 8)
    col0 = self._getString(0, 3, 6)
    col1 = self._getString(1, 4, 7)
    col2 = self._getString(2, 5, 8)
    dia1 = self._getString(0, 4, 8)
    dia2 = self._getString(6, 4, 2)
    if row0 == "000" or row1 == "000" or row2 == "000" or \
        col0 == "000" or col1 == "000" or col2 == "000" or \
        dia1 == "000" or dia2 == "000":
        return "0"
    elif row0 == "XXX" or row1 == "XXX" or row2 == "XXX" or \
        col0 == "XXX" or col1 == "XXX" or col2 == "XXX" or \
        dia1 == "XXX" or dia2 == "XXX":
        return "X"
    else:
        return ""
```

The method _getString expects the indexes of three squares as arguments. The method builds and returns a three-character string from the text in the squares at those positions.

```
def _getString(self, one, two, three):
    """Builds and returns a string from a row, column,
    or diagonal of the grid."""
    return self._grid[one].text() + self._grid[two].text() + \
           self._grid[three].text()
```

# Coding the Main Application Module

The program has one other module, where the main function is defined and called. This module is in the file tictactoeapp.py. The main function hides the system turtle, sets its