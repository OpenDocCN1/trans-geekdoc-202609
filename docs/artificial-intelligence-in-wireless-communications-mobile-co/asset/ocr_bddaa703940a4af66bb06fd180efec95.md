```
temp_int(i) = I;

sig(n) = mean(temp_sig);
int(n) = mean(temp_int);
sinr(n) = sig(n) - int(n);

std_sig(n) = std(temp_sig);
std_int(n) = std(temp_int);
std_sinr(n) = std_sig(n) - std_int(n);
```

```
n = n+1;

intpwr = 0.0:0.1:1.0;
fig = figure(1);
plot(intpwr, 'o-b', 'LineWidth', 2.0, 'MarkerFace', 'b', 'MarkerSize', 10)
hold on
plot(intpwr, sinr + std_sinr, 'k', 'MarkerFace', 'k')
plot(intpwr, sinr - std_sinr, 'k', 'MarkerFace', 'k')
```

```
xlabel('Interference Power (W)', 'FontSize', 20, 'FontWeight', 'bold');
ylabel('Estimated SINR (dB)', 'FontSize', 20, 'FontWeight', 'bold');
set(fig, 'Position', [100 1000 640])
set(gca, 'FontSize', 18);
set(gca, 'Position', [0.075 0.1 0.875 0.875])
leg = legend('Estimated SINR', 'Standard Deviation of Estimate');
```

```
fig = figure(2);
plot(intpwr, 'o-b', 'LineWidth', 2.0, 'MarkerFace', 'b', 'MarkerSize', 10)
hold on
plot(intpwr, sinr + std_sig, 'k', 'MarkerFace', 'k')
plot(intpwr, sinr - std_sig, 'k', 'MarkerFace', 'k')
```

```
xlabel('Interference Power (W)', 'FontSize', 20, 'FontWeight', 'bold');
ylabel('Estimated Signal Power (dBW)', 'FontSize', 20, 'FontWeight', 'bold');
set(fig, 'Position', [100 1000 640])
set(gca, 'FontSize', 18);
set(gca, 'Position', [0.075 0.1 0.875 0.875])
leg = legend('Estimated Signal Power', 'Standard Deviation of Estimate');
```