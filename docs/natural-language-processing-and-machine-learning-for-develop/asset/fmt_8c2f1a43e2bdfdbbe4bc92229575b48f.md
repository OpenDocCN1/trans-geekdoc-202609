
import pandas as pd import numpy as np df = pd.read_csv('sometext.csv', delimiter='\\t') print("=> First five rows (before):") print(df.head(5)) print("-------------------------") print() # map ham/spam to 0/1 values: df['type'] = df['type'].map({'ham':0, 'spam':1}) print("=> First five rows (after):") print(df.head(5)) print("-------------------------") 

[Listing 2.8](#ch02.xhtml#list2.8) initializes the data frame `df` with the contents of the CSV file `sometext.csv`, and then displays the contents of the first five rows by invoking `df.head(5)`, which is also the default number of rows to display.

The next code snippet in [Listing 2.8](#ch02.xhtml#list2.8) invokes the `map()` method to replace occurrences of ham with 0 and replace occurrences of spam with 1 in the column labeled `type`, as shown here:

```python
df['type'] = df['type'].map({'ham':0, 'spam':1})
```

The last portion of [Listing 2.8](#ch02.xhtml#list2.8) invokes the `head()` method again to display the first five rows of the dataset after having renamed the contents of the column `type`. Launch the code in [Listing 2.8](#ch02.xhtml#list2.8) and you will see the following output:

\=> First five rows (before): type                          text 0   ham                          Available only for today 1   ham           I'm joking with you 2  spam  Free entry in 2 a wkly comp 3   ham        U dun say so early hor 4   ham  I don't think he goes to usf \-------------------------   \=> First five rows (after):   type                          text 0     0     Available only for today 1     0           I'm joking with you 2     1  Free entry in 2 a wkly comp 3     0        U dun say so early hor 4     0  I don't think he goes to usf \------------------------- 

[Listing 2.9](#ch02.xhtml#list2.9) displays the contents of shirts.csv and [Listing 2.10](#ch02.xhtml#list2.10) displays the contents of shirts.py that illustrates four techniques for converting categorical data to numeric data.

***LISTING 2.9: shirts.csv***

type,ssize shirt,xxlarge shirt,xxlarge shirt,xlarge shirt,xlarge shirt,xlarge shirt,large shirt,medium shirt,small shirt,small shirt,xsmall shirt,xsmall shirt,xsmall 

***LISTING 2.10: shirts.py***

import pandas as pd shirts = pd.read_csv("shirts.csv") print("shirts before:") print(shirts) print() # TECHNIQUE #1: #shirts.loc[shirts['ssize']=='xxlarge','size'] = 4 #shirts.loc[shirts['ssize']=='xlarge', 'size'] = 4 #shirts.loc[shirts['ssize']=='large', 'size'] = 3 #shirts.loc[shirts['ssize']=='medium', 'size'] = 2 #shirts.loc[shirts['ssize']=='small', 'size'] = 1 #shirts.loc[shirts['ssize']=='xsmall', 'size'] = 1 # TECHNIQUE #2: #shirts['ssize'].replace('xxlarge', 4, inplace=True) #shirts['ssize'].replace('xlarge', 4, inplace=True) #shirts['ssize'].replace('large', 3, inplace=True) #shirts['ssize'].replace('medium', 2, inplace=True) #shirts['ssize'].replace('small', 1, inplace=True) #shirts['ssize'].replace('xsmall', 1, inplace=True) # TECHNIQUE #3: #shirts['ssize'] = shirts['ssize'].apply({'xxlarge':4, 'xlarge':4, 'large':3, 'medium':2, 'small':1, 'xsmall':1}.get) # TECHNIQUE #4: shirts['ssize'] = shirts['ssize'].replace(regex='xlarge', value=4) shirts['ssize'] = shirts['ssize'].replace(regex='large', value=3) shirts['ssize'] = shirts['ssize'].replace(regex='medium', value=2) shirts['ssize'] = shirts['ssize'].replace(regex='small', value=1) print("shirts after:") print(shirts) 

[Listing 2.10](#ch02.xhtml#list2.10) starts with a code block of six statements that uses direct comparison with strings to make numeric replacements. For example, the following code snippet replaces all occurrences of the string xxlarge with the value 4:

shirts.loc[shirts['ssize']=='xxlarge','size'] = 4 

The second code block consists of six statements that use the replace() method to perform the same updates, an example of which is shown here:

shirts['ssize'].replace('xxlarge', 4, inplace=True) 

The third code block consists of a single statement that use the apply() method to perform the same updates, as shown here:

shirts['ssize'] = shirts['ssize'].apply({'xxlarge':4, 'xlarge':4, 'large':3, 'medium':2, 'small':1, 'xsmall':1}.get) 

The fourth code block consists of four statements that use regular expressions to perform the same updates, an example of which is shown here:

shirts['ssize'] = shirts['ssize'].replace(regex='xlarge', value=4) 

Since the preceding code snippet matches xxlarge as well as xlarge, we only need four statements instead of six statements. If you are unfamiliar with regular expressions, you can read Appendix C. Now launch the code in [Listing 2.10](#ch02.xhtml#list2.10) and you will see the following output:

shirts before   type   size 0   shirt  xxlarge 1   shirt  xxlarge 2   shirt   xlarge 3   shirt   xlarge 4   shirt   xlarge 5   shirt    large 6   shirt   medium 7   shirt    small 8   shirt    small 9   shirt   xsmall 10  shirt   xsmall 11  shirt   xsmall   shirts after:   type  size 0   shirt     4 1   shirt     4 2   shirt     4 3   shirt     4 4   shirt     4 5   shirt     3 6   shirt     2 7   shirt     1 8   shirt     1 9   shirt     1 10  shirt     1 11  shirt     1 

## **Matching and Splitting Strings in Pandas**

[Listing 2.11](#ch02.xhtml#list2.11) displays the contents of shirts_str.py that illustrates how to match a column value with an initial string and also how to split a column value based on a letter.

***LISTING 2.11: shirts_str.py***

import pandas as pd shirts = pd.read_csv("shirts.csv") print("shirts:") print(shirts) print() print("shirts starting with xl:") print(shirts[shirts.ssize.str.startswith('xl')]) print() print("Exclude 'xlarge' shirts:") print(shirts[shirts['ssize'] != 'xlarge']) print() print("first three letters:") shirts['sub1'] = shirts['ssize'].str[:3] print(shirts) print() print("split ssize on letter 'a':") shirts['sub2'] = shirts['ssize'].str.split('a') print(shirts) print() print("Rows 3 through 5 and column 2:") print(shirts.iloc[2:5, 2]) print() 

[Listing 2.11](#ch02.xhtml#list2.11) initializes the data frame `df` with the contents of the CSV file `shirts.csv`, and then displays the contents of `df`. The next code snippet in [Listing 2.11](#ch02.xhtml#list2.11) uses the `startswith()` method to match the shirt types that start with the letters `xl`, followed by a code snippet that displays the shorts whose size does not equal the string `xlarge`.

The next code snippet uses the construct `str[:3]` to display the first three letters of the shirt types, followed by a code snippet that uses the `split()` method to split the shirt types based on the letter “a.”

The final code snippet invokes `iloc[2:5,2]` to display the contents of rows 3 through 5 inclusive, and only the second column. The output of [Listing 2.11](#ch02.xhtml#list2.11) is here:
