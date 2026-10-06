# CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

```
# variable declaration and assignment
num1 = 10 # int type
num2 = 99 # int type
num3 = 1.5 # float type
decision = True # bool type
reason = "because" # str type
nums_list = [num1, num2, num3] # list type
nums_dict = {'num1': num1, 'num2': num2, 'num3': num3} # dict type

# mathematical operators
two_nums_sum = num1 + num2
two_nums_diff = num2 - num1
two_nums_prod = num1 * num2
two_nums_quot = num2 / num1
two_nums_pow = num2 ^ num1
two_nums_mod = num2 % num1

# if-else
if num1 >= num2:
    new_var = "bigger"
elif num1 == num2:
    new_var = "same"
else:
    new_var = "smaller"

# looping: for loop
running_sum = 0
for num in range(num1):
    running_sum += num

# looping with a condition: while loop
counter = 1
while counter <= 10:
    print("Hello time " + counter)
    counter += 1

# function declaration and use
def lopsided_square(var):
    var_square = var * var + 1
    return var_square

lopsided_square(num1)
```

Figure 11-2. Some example Python code