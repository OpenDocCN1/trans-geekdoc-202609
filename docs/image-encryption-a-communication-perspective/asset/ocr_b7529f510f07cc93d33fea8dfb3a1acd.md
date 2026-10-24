```
if rbstartcol(rb)>rbendcol(rb)
    c = 0;
    d = -1;
else
    c = 1;
    d = 1;
end
col = (rbendrow(rb) -
    rbstartrow(rb))*(n(cb)-1-
    maxcol(rb))+(rbendrow(rb)-newindexquot
ient(i,j)+c)+(maxcol(rb)-
    newindexmod(i,j))*(rbendrow(rb)-
    rbstartrow(rb)+d);
else%if newindexmod(i,j)<= mincol(rb)
    col = I-mincol(rb)*(rbendrow(rb)-
    rbstartrow(rb))+(rbendrow(rb)-newindex
-quotient(i,j)+1)+(mincol(rb)-1-
    newindexmod(i,j))*(rbendrow(rb)-
    rbstartrow(rb));
end
    row = 1+I-N(cb+1)+rowblockindex(i,j);
end
end
    pr(i,j+N(cb)-1) = row;
    pc(i,j+N(cb)-1) = col;
end
end
end

function out = chaoperm(im,pr,pc,num,forward)

%
[rows,cols] = size(im);
mat = zeros([rows,cols,num+1]);
mat(:,:,1) = im(:,:,);
for loc = 2:num+1
if(strcmp(forward,'forward'))
    for i = 1:rows
        for j = 1:cols
            mat(pr(i,j),pc(i,j),loc) =
            mat(i,j,loc-1);
        end
    end
elseif(strcmp(forward,'backward'))
    for i = 1:rows
```