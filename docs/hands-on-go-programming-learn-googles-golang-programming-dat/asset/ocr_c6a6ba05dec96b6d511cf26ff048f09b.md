# 12.4 Best practice

It is not a good practice to call panic explicitly in program logic. The caller of your function will not know that your function can panic and so, the caller may not write the recover function. In that case, the whole program will terminate. It is always the best practice to return an error from the function instead of calling panic explicitly.

When a function returns an error, we should handle that error. We should not ignore it.