# Biological Pattern Discovery with R

and were used to take part in an operation. After values one and three were popped up, S = 7. The product value of one and three was pushed back to the stack. Therefore, S = (7, 3). The last token in the RPN string was an operator (a). Therefore two entries (7 and 3) were popped up from the stack to take part in an operation. The summed value, which was ten, was pushed back to the stack. At this time, the stack was composed of only one value and all the tokens in an RPN string have been scanned. The unique value in the stack (ten) was the final result.

| x | 3 | y | * | + | x | z | * | + |
|---|---|---|---|---|---|---|---||
| | | 3 | | | 1 | 3 | |
| 1 | 1 | 6 | | 7 | 1 | 7 | 10 |

Fig. 8. The stack used for parsing an RPN string for the evaluation.

rpn='x3y*+xz*+'
values=c(1,2,3)
names(values)=c('x','y','z')
operators=c('*','+')
stk=NULL
for(i in 1:nchar(rpn))
{
  token=substr(rpn,i,i)
  if(length(which(operators==token))>0)
  {
    pops=pop(stk[length(stk):(length(stk)-1)])
    stk=stk[-length(stk):(length(stk)-1))]
    if(token=='+') stk=c(stk,prod(pops))
    if(token=='*') stk=c(stk,sum(pops))
  } else {
    variable=which(names(values)==token)
    if(length(variable)>0)
    {
      stk=c(stk,values[variable])
    } else {
      stk=c(stk,as.numeric(token))
    }
  }
}