```
```matlab
change = inf;
temp = exp(x*w);
ll = -0.5*w'*w + sum(t.*log(temp) - temp);
while change > 1e-3
    % Compute gradient
    temp = exp(x*w);
    gra = -w + sum(repmat(t,1,2).*x - repmat(temp,1,2).*x,1)';
    % Compute Hessian
    hess = -eye(2) - x'*(x.*repmat(temp,1,2));
    % Update w
    neww = w - inv(hess)*gra;
    % Compute change
    change = sum((neww-w).^2);
    w = neww;

    % Store all of the w
    wall = [wall;w'];
    % Compute the likelihood (should always increase)
    temp = exp(x*w);
    ll = [ll;-0.5*w'*w + sum(t.*log(temp) - temp)];
end

%% Metropolis-Hastings
% Initialise w
wm = randn(2,1);
temp = exp(x*wm);
wall_m = [];
% Compute old log posterior
oldll = -0.5*wm'*wm + sum(t.*log(temp) - temp);
for s = 1:10000 % Generate 10000 samples
    % Propose a new candidate
    wnew = wm + randn(2,1)*0.1; % Gaussian proposal, std = 0.1
    % Compute new log likelihood
    temp = exp(x*wnew);
    newll = -0.5*wnew'*wnew + sum(t.*log(temp) - temp);
    % Accept or reject
    if rand<exp(newll-oldll)
        wm = wnew;
        oldll = newll;
    end
    % Store all w
    wall_m = [wall_m;wm'];
end

%% Plot samples
% No thinning or ignoring of burn-in
figure(1);
hold off
plot(wall_m(:,1),wall_m(:,2),'k.','color',[0.6 0.6 0.6])

%% Plot the approximate posterior
% Compute posterior (negative inverse of Hessian)
gcov = -inv(eye(2) - x'*(x.*repmat(temp,1,2)));
% Evaluate over a set of points
[W1,W2] = meshgrid(-1:0.01:1,[-1:0.01:1]);
gli = 1./(sqrt(2*pi)*det(gcov)).*repmat(1,size(W1));
for i = 1:size(W1,1)
    for j = 1:size(W1,2)
```
```