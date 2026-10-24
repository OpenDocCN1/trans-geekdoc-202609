```
```matlab
else
        phi = phi/(norm(phi)*sqrt(dx)); % Rescale result
end

if nargin > 2
        phi2 = phi(1: 2: end); % phi2 is approximately
                phi(2x)
        if length(c) == 2
                L = length(phi2);
        else
                L = ceil(0.5/dx);
        end

        % Construct psi from translates of phi2
        c = g{1};
        psi = zeros(length(phi2)+L*(length(c)-1),1);
        x2 = (0: length(psi)-1)*dx - g{2} - 0*h{2}/2;

        for k = 1: length(c)
                i = (1: length(phi2)) + L*(k-1);
                psi(i) = psi(i) + c(k)*phi2;
        end
end
return;

function s = filterstr(a,K)
% Convert a filter to a string
[n,d] = rat(K/sqrt(2));
if d < 50
        a{1} = a{1}/sqrt(2); % Scale filter by sqrt(2)
        s = '{';
else
        s = '';
end

Scale = [pow2(1: 15),10,20,160,280,inf];

for i = 1: length(Scale)
        if norm(round(a{1}*Scale(i))/Scale(i) -
                a{1},inf) < 1e-9
                a{1} = a{1}*Scale(i); % Scale filter by a
                        power of 2 or 160
                s = '[';
                break;
        end
end
```
```